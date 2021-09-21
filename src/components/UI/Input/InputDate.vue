<template>
  <div class="date">
    <div class="input-date">
      <input 
        type="date" 
        @input="date = $event.target.value"
        v-model="date"
        @change="addDateClick"
      />
      {{date}}
    </div>
  </div>
</template>

<script>
export default {
  name: 'InputDate',
  data() {
    return {
      date: 'Выберите дату',
      isBtnDelete: true
    }
  },
  methods: {
    addDateClick(event) {
      this.date = new Date(event.target.value).toLocaleDateString()
    }
  },
  mounted() {
    if (localStorage.date) {
      this.date = localStorage.date
    }
  },
  watch: {
    date(newDate) {
      localStorage.date = newDate
    }
  }
}
</script>

<style scoped>
  .btn-delete {
    margin: 0 .5rem;
    background: url('../../../assets/delete.svg') no-repeat;
    border: none;
    outline: none;
    width: 27px;
    height: 20px;
    background-size: 50%;
  }

  .btn-delete:hover,
  .btn-delete:focus {
    opacity: .5;
    transition: opacity .5s;
  }

  .date {
    border-bottom: 1px solid #41A39D;
    padding: .5rem 0;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .input-date {
    display: flex;
    align-items: center;
  }

  .input-date input {
    border: none;
    background: inherit;
    outline: none;
    cursor: pointer;
    margin-right: 1rem;
  }

  ::-webkit-datetime-edit { display: none; }
  ::-webkit-datetime-edit-fields-wrapper { display: none;}
  ::-webkit-datetime-edit-text { display: none;}
  ::-webkit-datetime-edit-month-field { display: none;}
  ::-webkit-datetime-edit-day-field { display: none;}
  ::-webkit-datetime-edit-year-field { display: none; }
  ::-webkit-inner-spin-button { display: none; }
  ::-webkit-calendar-picker-indicator { 
    background: url('../../../assets/date.svg') no-repeat;
    cursor: pointer;
    background-size: 80%;
    /* width: 27px;
    height: 29px; */
}
</style>