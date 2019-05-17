<template>
  <div id="app">
    <!-- Форма, в которой вместо отправления данных
         вызывается функция alertSum -->
    <form @submit.prevent="alertSum">
      <label>First Value</label> <br />
      <input type="text" name="first_text_field" placeholder="1.01" v-model="firstValue">
      <br />

      <label>Second Value</label> <br />
      <input type="text" name="second_text_field" placeholder="1.01" v-model="secondValue">
      <br />
      <input class="btn" type="submit" value="Show Sum">
    </form>
  </div>
</template>

<script>
export default {
  name: 'app',

  data() {
    return {
      firstValue: '',
      secondValue: '',
    };
  },

  methods: {
    /**
     * Функция проверяет на правильность введённые данные
     * и выводит в всплывающем окне сумму введённых чисел
     */
    alertSum() {
      /**
       * Провереям содержит ли первое и второе введённое значение
       * что-то, кроме символов цифр.
       * Также проверяем пусто ли хотя бы одно из введённых значений
       */
      if (
        this.firstValue.match(/[^0-9.]/gi)
        || this.secondValue.match(/[^0-9.]/gi)
        || this.firstValue === ''
        || this.secondValue === ''
      ) {
        // Предупреждаем о неккоректности данных
        alert('Incorrect data');
      } else {
        // Выводим сумму
        alert(parseFloat(this.firstValue) + parseFloat(this.secondValue));
      }
    },
  },
};
</script>

<style>
form {
        background-color: khaki;
        display: block;
        margin: auto;
        width: 20%;
}

input, label, .btn {
        width: 90%;
        margin: 4px;
}

.btn {
        margin-left: 5%;
}

</style>
