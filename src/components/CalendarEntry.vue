<template>
  <div class="container mt-5">
    <div class="row">
      <div class="col-6 offset-3">
        <div class="card">
          <div class="card-header text-center bg-vue">
            <h5>Neuer Termin für: <strong>{{ getNameOfActiveDay }}</strong></h5>
          </div>
          <div class="card-body text-center">
            <input
              type="text"
              class="form-control"
              placeholder="Neuer Termin"
            />
            <div class="mt-3 text-center">
              <span
                v-for="(color, index) in [
                  'primary',
                  'success',
                  'info',
                  'warning',
                  'danger',
                ]"
                :key="index"
                class="alert mr-2 square"
                :class="[
                  eventColor === color ? getBorderColor : '',
                  'alert-' + color,
                ]"
                style="cursor: pointer"
                @click="changeEventColor"
              ></span>
            </div>
            <hr />
            <button class="btn bg-vue2 btn-block">Eintragen</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { store } from '../store.js';


export default {
  name: "CalendarEntry",
  data() {
    return {
      eventColor: "primary",
    };
  },
  methods:  {
      changeEventColor: function(color) {
          this.eventColor = color;
      }
  },
  computed: {
    getBorderColor() {
      return "border border-" + this.eventColor;
    },
    getNameOfActiveDay() {
        return store.getActiveDay();
    }
  },
};
</script>

<style scoped>
.bg-vue2 {
  background-color: cadetblue;
}
.square {
  width: 40px;
  height: 40px;
}
</style>
