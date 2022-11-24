<template>
  <div class="main">
    <img class="bg" src="../../assets/images/sabu1.jpg" />
    <p class="saburo-text">さぶろうの誕生日を入力して下さい</p>
    <div class="inputs">
      <input
        ref="r1"
        class="input-birthday"
        type="number"
        max="1"
        size="1"
        @input="
          value.month[1] = $event.target.value
          $refs.r2.focus()
        "
      />
      <input
        ref="r2"
        class="input-birthday"
        type="number"
        @input="
          value.month[2] = $event.target.value
          $refs.r3.focus()
        "
      />
      <p class="input-birthday-text">月</p>
      <input
        ref="r3"
        class="input-birthday"
        type="number"
        @input="
          value.date[1] = $event.target.value
          $refs.r4.focus()
        "
      />
      <input
        ref="r4"
        class="input-birthday"
        type="number"
        @input="value.date[2] = $event.target.value"
      />
      <p class="input-birthday-text">日</p>
    </div>
    <button class="ok-button" @click="check">OK</button>
    <div v-if="showOk" class="overlay">
      <div class="window">
        <p class="popup-text">正解！！</p>
        <nuxt-link class="next" to="/yotsu">次へ</nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      birthday: {
        month: {
          1: 1,
          2: 2,
        },
        date: {
          1: 1,
          2: 9,
        },
      },
      value: {
        month: {
          1: null,
          2: null,
        },
        date: {
          1: null,
          2: null,
        },
      },
      showOk: false,
      showNo: false,
    }
  },
  methods: {
    check() {
      if (
        this.birthday.month[1] === Number(this.value.month[1]) &&
        this.birthday.month[2] === Number(this.value.month[2]) &&
        this.birthday.date[1] === Number(this.value.date[1]) &&
        this.birthday.date[2] === Number(this.value.date[2])
      ) {
        this.showOk = true
      } else {
        this.showNo = true
      }
    },
  },
}
</script>

<style scoped>
.main {
  height: 100%;
  width: 100%;
}
.input-birthday {
  width: 60px;
  height: 60px;
  text-align: center;
  font-size: 31px;
  border-radius: 16px;
}
.input-birthday-text {
  display: inline-block;
}

.ok-button {
  display: block;
  text-align: center;
  margin: auto;
  width: 180px;
  margin-top: 50px;
  height: 45px;
  border-radius: 19px;
  background-color: #5e2b2b;
  color: white;
}

.saburo-text {
  font-weight: bold;
  margin: 20px 0;
  text-align: center;
  margin-top: 100px;
}

.inputs {
  display: table;
  margin: auto;
}
.input-birthday {
  margin: 4px;
}
.bg {
  position: absolute;
  top: 0;
  z-index: -1;
  opacity: 0.4;
}

.open {
  cursor: pointer; /* マウスオーバーでカーソルの形状を変えることで、クリックできる要素だとわかりやすいように */
}
#pop-up {
  display: none; /* label でコントロールするので input は非表示に */
}

.overlay {
  display: block;
  z-index: 9999;
  background-color: #00000070;
  position: fixed;
  width: 100%;
  height: 100vh;
  top: 0;
  left: 0;
}
.window {
  width: 266px;
  height: 240px;
  background-color: #ffffff;
  border-radius: 6px;
  justify-content: center;
  align-items: center;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.next {
  display: block;
  width: 100px;
  text-align: center;
  margin: 40px auto;
  padding-top: 6px;
  background-color: #5e2b2b;
  border-radius: 11px;
  color: white;
  height: 35px;
}

.popup-text {
  text-align: center;
  margin-top: 68px;
  font-size: 27px;
  font-weight: bold;
}
</style>
