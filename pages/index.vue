<template>
  <section class="section">
    <div class="card">
      <div class="card-content">
        <div class="content has-text-centered">
          <div class="columns">
            <h3>Pencarian Penerbangan</h3>
          </div>
          <div class="columns">
            <div class="column">
              <b-field label="Kota Keberangkatan">
                <b-autocomplete
                  rounded
                  v-model="name"
                  :data="filteredDataObj"
                  field="schedule.bandaraKeberangkatan.kota"
                  placeholder="e.g. Jakarta"
                  icon="magnify"
                  clearable
                  @select="(option) => (selected = option)"
                >
                  <template #empty>No results found</template>
                </b-autocomplete>
              </b-field>
            </div>
            <div class="column">
              <b-field label="Kota Tujuan">
                <b-input
                  rounded
                  type="text"
                  name="tujuan"
                  id=""
                  placeholder="Kemana tujuan anda ?"
                />
              </b-field>
            </div>
            <div class="column">
              <b-field label="Waktu Kedatangan">
                <b-datetimepicker
                  rounded
                  placeholder="Click to select..."
                  icon="calendar-today"
                  :locale="locale"
                  :datepicker="{ showWeekNumber }"
                  :timepicker="{ enableSeconds, hourFormat }"
                  horizontal-time-picker
                >
                </b-datetimepicker>
              </b-field>
            </div>
          </div>
          <div class="columns">
            <div class="column">
              <b-field label="Jumlah penumpang">
                <b-numberinput rounded v-model="number"></b-numberinput>
              </b-field>
            </div>
            <div class="column">
              <b-field label="Seat Class">
                <b-select placeholder="Select a seat class" rounded>
                  <option value="ekonomi">Ekonomi</option>
                  <option value="bisnis">Bisnin</option>
                  <option value="eksekutif">Eksekutif</option>
                </b-select>
              </b-field>
            </div>
            <div class="column">
              <b-collapse :open="false" aria-id="contentIdForA11y1">
                <template #trigger>
                  <b-field>
                    <b-switch :value="false"> Round Trip </b-switch>
                  </b-field>
                </template>
                <b-field label="Waktu Pulang">
                  <b-datetimepicker
                    rounded
                    placeholder="Click to select..."
                    icon="calendar-today"
                    :locale="locale"
                    :datepicker="{ showWeekNumber }"
                    :timepicker="{ enableSeconds, hourFormat }"
                    horizontal-time-picker
                  >
                  </b-datetimepicker>
                </b-field>
              </b-collapse>
            </div>
          </div>
          <div class="columns">
            <b-button @click="setTest()" type="is-primary">Cari</b-button>
          </div>
        </div>
      </div>
    </div>
    <div class="column">
      <card v-for="schedule of model" :key="schedule.id">
        <div class="columns">
          <div class="column">
            <div class="columns">
              <img
                :src="schedule.maskapai.logo"
                :alt="schedule.maskapai.nama"
              />
            </div>
            <div class="columns">{{ schedule.maskapai.nama }}</div>
          </div>
          <div class="column">
            <div class="columns">{{ schedule.bandaraKeberangkatan.kota }}</div>
            <div class="columns">{{ schedule.waktuKeberangkatan }}</div>
          </div>
          <div class="column">
            <div class="columns">{{ schedule.bandaraKedatangan.kota }}</div>
            <div class="columns">{{ schedule.waktuKedatangan }}</div>
          </div>
          <div class="column">
            <div class="columns">{{ schedule.hargaTiket }}</div>
            <div class="columns">
              <nuxt-link
                class="button is-link is-small"
                :to="{ path: 'detail', query: { id: schedule.id } }"
                >Select</nuxt-link
              >
            </div>
          </div>
        </div>
      </card>
    </div>
  </section>
</template>

<script>
import Card from '~/components/Card.vue'

export default {
  name: 'HomePage',

  components: {
    Card,
  },
  data() {
    return {
      data: [
        'Jakarta',
        'Bandung',
        'Surabaya',
        'Makassar',
        'Yogyakarta',
        'Palembang',
      ],
      showWeekNumber: false,
      enableSeconds: false,
      hourFormat: undefined, // Browser locale
      locale: undefined, // Browser locale
      name: '',
      test: '',
      selected: null,
      number: 0,
      model: null,
    }
  },
  methods: {
    setTest() {
      this.test = 'cobaa'
    },
    async list() {
      this.model = await fetch(
        'http://localhost:3333/api/v1/schedules',
        {}
      ).then((res) => res.json())
    },
  },
  mounted() {
    this.list()
  },
  computed: {
    ffilteredDataObj() {
      return this.model.filter((option) => {
        return (
          option.schedule.bandaraKeberangkatan.kota
            .toString()
            .toLowerCase()
            .includes(this.name.toLowerCase()) >= 0
        )
      })
    },
  },
}
</script>
<style>
img {
  width: 128px;
}
</style>
