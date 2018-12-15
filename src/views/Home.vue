<template>
  <div>
    <header class="Header">{{title}}</header>

    <div class="Main">
      <table>
        <thead>
          <tr>
            <th v-for="item of data" :key="item.alias">{{item.alias}}</th>
          </tr>
        </thead>

        <tbody>
          <tr>
            <td v-for="item of data" :key="item.alias">
            <router-link :to="{name: 'quest', params: {id: item.alias}}">
              <i :class="define(item.status)"></i>
            </router-link>
            </td>
          </tr>
        </tbody>
      </table>

    </div>
  </div>
</template>

<script>
// (item.status !== 'NO_DATA' ? item.alias : 'NO_DATA')

const data = function() {
  return {
    title: 'Games list',
    data: '',
    define: function(data) {
      switch(data) {
        case 'SUCCESS':
          return 'fas fa-times';

        case 'CRASH':
          return 'fas fa-check';

        default:
          return 'fas fa-minus'
      }
    },
  }
}

function created() {
  fetch('./server/MainPageInfo.json')
    .then(response => {
      return response.json()
    })
    .then(data => {
      this.data = data;
    })
    .catch(err => console.log('Error: ' + err.message));
}

export default {
  name: 'home',
  data: data,
  created: created
};

</script>

<style scoped lang='sass'>
$light: #fcfaf9
$dark: #1c1c1c

.Header
  width: 100%
  min-height: 130px
  font-size: 1.5rem
  line-height: 130px
  color: $light
  background: $dark

.Main
  margin: 100px auto
</style>
