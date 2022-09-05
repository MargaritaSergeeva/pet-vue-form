<template>
  <div class="container">
    <form class="card" @submit.prevent="sendForm">
      <h1>Анкета на Vue разработчика!</h1>
      <app-input
        v-model="name"
        label="Как тебя зовут?"
        placeholder="Введи имя"
        :error="errors.name"
      ></app-input>

      <div class="form-control">
        <label for="age">Выбери возраст</label>
        <input v-model.number="age" type="number" id="age" max="70">
      </div>

      <div class="form-control">
        <label for="city">Твой город</label>
        <select id="city" v-model="city">
          <option value="spb">Санкт-Петербург</option>
          <option value="msk">Москва</option>
          <option value="kzn">Казань</option>
          <option value="nsk">Новосибирск</option>
        </select>
      </div>

      <div class="form-checkbox">
        <span class="label">Готов к переезду в Токио?</span>
        <div class="checkbox">
          <label><input v-model="relocate" type="radio" name="trip" value="yes" /> Да</label>
        </div>

        <div class="checkbox">
          <label><input v-model="relocate" type="radio" name="trip" value="no" /> Нет</label>
        </div>
      </div>

      <div class="form-checkbox">
        <span class="label">Что знаешь во Vue?</span>
        <div class="checkbox">
          <label><input v-model="skills" name="skills" type="checkbox" value="vuex" /> Vuex</label>
        </div>
        <div class="checkbox">
          <label><input v-model="skills" name="skills" type="checkbox" value="cli" /> Vue CLI</label>
        </div>
        <div class="checkbox">
          <label><input v-model="skills" name="skills" type="checkbox" value="router" /> Vue Router</label>
        </div>
      </div>

      <div class="form-checkbox">
        <span class="label">Правила компании</span>
        <div class="checkbox">
          <label><input v-model="agree" name="agree" type="checkbox" /> с правилами согласен</label>
        </div>
      </div>

      <button type="submit" class="btn primary">Отправить</button>
    </form>
  </div>
</template>

<script>
import AppInput from '@/AppInput'

export default {
  data () {
    return {
      name: '',
      age: 23,
      city: 'msk',
      relocate: 'yes',
      skills: [],
      agree: false,
      errors: {
        name: null
      }
    }
  },
  methods: {
    isFormValid () {
      let isValid = true
      if (this.name.length === 0) {
        this.errors.name = 'Введите имя'
        isValid = false
      } else {
        this.errors.name = null
      }
      return isValid
    },
    sendForm () {
      if (this.isFormValid()) {
        console.group('Form Data')
        console.log('Name: ', this.name)
        console.log('Age: ', this.age)
        console.log('City: ', this.city)
        console.log('Relocate: ', this.relocate)
        console.log('Skills: ', this.skills)
        console.log('Agree: ', this.agree)
        console.groupEnd()
      }
    }
  },
  components: {
    AppInput
  }
}
</script>

<style>

.form-control small {
  color: #e53935;
}

.form-control.error input {
  border-color: #e53935;
}

</style>
