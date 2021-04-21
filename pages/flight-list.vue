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
              <b-field label="Kota Tujuan">
                <b-input
                  rounded
                  type="text"
                  name="tujuan"
                  id=""
                  placeholder="Kemana Tujuan Anda ?"
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
            <div class="column">
              <b-button type="is-primary is-large">Cari</b-button>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="column">
      <card>
        <div class="columns">
          <div class="column">
            <div class="columns">
              <img
                src="http://3.bp.blogspot.com/-vb-i2NBCHps/TzJrLrHrMiI/AAAAAAAAE60/gvjsKAo25tM/s1600/LOGO+GARUDA+INDONESIA+AIR.png"
                alt="Garuda Indonesia"
              />
            </div>
            <div class="columns">Garuda Indonesia</div>
          </div>
          <div class="column">
            <div class="columns">Jakarta</div>
            <div class="columns">Fri, 9th April 2021 - 17:00</div>
          </div>
          <div class="column">
            <div class="columns">Surabaya</div>
            <div class="columns">Fri, 9th April 2021 - 17:45</div>
          </div>
          <div class="column">
            <div class="columns">IDR {{ 670000 | currency }}</div>
            <div class="columns">
              <nuxt-link class="button is-link is-small" to="detail/1"
                >Select</nuxt-link
              >
            </div>
          </div>
        </div>
      </card>
      <card>
        <div class="columns">
          <div class="column">
            <div class="columns">
              <img
                src="data:image/png;base64,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"
                alt="Citilink"
              />
            </div>
            <div class="columns">Citilink</div>
          </div>
          <div class="column">
            <div class="columns">Jakarta</div>
            <div class="columns">Fri, 9th April 2021 - 12:00</div>
          </div>
          <div class="column">
            <div class="columns">Surabaya</div>
            <div class="columns">Fri, 9th April 2021 - 12:45</div>
          </div>
          <div class="column">
            <div class="columns">IDR 670000</div>
            <div class="columns">
              <nuxt-link class="button is-link is-small" to="detail/1"
                >Select</nuxt-link
              >
            </div>
          </div>
        </div>
      </card>
      <card>
        <div class="columns">
          <div class="column">
            <div class="columns">
              <img
                src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTwyQIAVG4oSwUxRONmh98B-21fbBCJb_aoXw&usqp=CAU"
                alt="Lion Air"
              />
            </div>
            <div class="columns">Lion Air</div>
          </div>
          <div class="column">
            <div class="columns">Jakarta</div>
            <div class="columns">Fri, 9th April 2021 - 07:00</div>
          </div>
          <div class="column">
            <div class="columns">Surabaya</div>
            <div class="columns">Fri, 9th April 2021 - 07:45</div>
          </div>
          <div class="column">
            <div class="columns">IDR 670000</div>
            <div class="columns">
              <nuxt-link class="button is-link is-small" to="detail/1"
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
  name: 'Flight-List',

  components: {
    Card,
  },
}
</script>
<style>
img {
  width: 64px;
}
</style>
