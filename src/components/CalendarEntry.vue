<template>
  <div class="container mt-5">
    <div class="row">
      <div class="col-6 offset-3">
        <div class="card">
          <div class="card-header text-center bg-vue">
            <h5>Neuer Termin für: <strong>{{ getNameOfActiveDay }}</strong></h5>
          </div>
          <div class="card-body">
            <input
              type="text"
              class="form-control"
              placeholder="Neuer Termin"
              v-model='eventTitle'
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
                  'alert-' + color
                ]"
                style="cursor: pointer"
                @click="changeEventColor(color)"
              ></span>
            </div>
            <hr />
            <button class="btn bg-vue2 btn-block"
            @click="storeEvent(eventTitle)"
            >Eintragen</button>
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
      eventTitle: ""
    };
  },
  computed: {
    getBorderColor() {
      return "border border-" + this.eventColor;
    },
    getNameOfActiveDay() {
        return store.getActiveDay().fullName;
    }
  },
  methods:  {
      changeEventColor: function(color) {
          this.eventColor = color;
      }
   },
   storeEvent: function(eventTitle, eventColor) {
     store.storeEvent(eventTitle, eventColor);
     this.eventTitle=';'
   }
  }
</script>

<style scoped>
.bg-vue2 {
  background-color: rgb(65, 184, 131);
  color: white;
}
.square {
  width: 40px;
  height: 40px;
}
</style>
