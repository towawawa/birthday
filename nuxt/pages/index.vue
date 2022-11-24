<template>
  <div>
    <p>さぶろうの誕生日を入力して下さい</p>
    <input type="number" @input="value.month = $event.target.value" />
    <p>月</p>
    <input type="number" @input="value.date = $event.target.value" />
    <p>日</p>
    <button @click="check">OK</button>
    <p v-if="showOk">正解！！</p>
    <p v-if="showNo">不正解</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      birthday: {
        month: 12,
        date: 19,
      },
      value: {
        month: null,
        date: null,
      },
      showOk: false,
      showNo: false,
    }
  },
  methods: {
    check() {
      if (
        this.birthday.month === Number(this.value.month) &&
        this.birthday.date === Number(this.value.date)
      ) {
        this.showOk = true
      } else {
        this.showNo = true
      }
    },
  },
}
</script>
