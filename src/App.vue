<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <h2>Доступы</h2>
    <treeOuter :array='startArray'/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import treeOuter from './components/treeOuter.vue';

@Component({
  components: {
    treeOuter,
  },
})
export default class App extends Vue {
  startArray = [
        {id: 1 , checked: false, parentid: 0, name: 'Доступ в CRM'},
        {id: 4 , checked: false, parentid: 2, name: 'Изменине почты'},
        {id: 3 , checked: false, parentid: 8, name: 'Изменение пароля'},
        {id: 5 , checked: false, parentid: 6, name: 'Смена аватарки'},
        {id: 6 , checked: false, parentid: 0, name: 'Доступ к чату'},
        {id: 2 , checked: false, parentid: 1, name: 'Просмотр информации о пользователе'},
        {id: 7 , checked: false, parentid: 6, name: 'Платежи'},
        {id: 8 , checked: false, parentid: 7, name: 'Прием платежей'},
        {id: 9 , checked: false, parentid: 7, name: 'Отправка платежей'},
        {id: 10 , checked: false, parentid: 7, name: 'Вывод средств'},
        {id: 11 , checked: false, parentid: 7, name: 'Прием платежей'}
  ]
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
