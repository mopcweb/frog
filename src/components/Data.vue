<template>
    <div class="Quest">
        <router-link to="/">Go home</router-link>

        <table>
          <caption>Quest: {{title}}</caption>
          <thead>
            <tr>
              <th>Build ID</th>
              <th>Platform</th>
              <th>Quest Name</th>
            </tr>
          </thead>

          <tbody>
            <tr>
              <td>{{data.globalId}}</td>
              <td>{{data.platform}}</td>
              <td>{{data.name}}</td>
            </tr>
          </tbody>
        </table>

        <h2>Pathways</h2>

        <table class="Details">
          <thead>
            <tr>
              <th>Status</th>
              <th>Path Name</th>
              <th>Leafs Info</th>
            </tr>
          </thead>

          <tbody>
            <tr>
              <td>{{data.pathway.status}}</td>
              <td>{{data.pathway.name}}</td>
              <td v-html="defineLeafs(pathed, allleafs)"></td>
            </tr>
          </tbody>
        </table>

    </div>
</template>

<script>
const data = function() {
  return {
    defineLeafs: function(pathed, allleafs) {
      // New empty array for pushing there pathed leafs
      let arr = [];

      // Check each leaf if in pathed leafs array
      allleafs.map(leaf => {
        pathed.indexOf(leaf) !== -1 ? arr.push(leaf) : ''
      });

      // Change data of each pathed leaf with check icon & commas between them with arrows
      let check = arr.map(() => '<i class="fas fa-check"></i>').join(',').replace(/,/gi, ' <i class="fas fa-long-arrow-alt-right"></i> ')

      return check
    },
  }
};

export default {
  name: 'quest',
  data: data,
  props: ['data', 'pathed', 'allleafs', 'title']
};

</script>

<style lang='sass'>
.Quest
  margin-bottom: 100px
  padding-left: 70px

  &:last-of-type
    margin: 0

  a
    position: fixed
    top: 0
    left: 0
    padding-left: 20px
    display: block
    width: 70px
    height: 100%
    font-size: 1.5rem
    color: #fcfaf9
    writing-mode: vertical-lr
    text-orientation: sideways
    text-decoration: none
    text-align: center
    background: #1c1c1c
    transform: rotate(180deg)
    transition: all 0.3s

    &:hover
      padding-left: 15px
      font-size: 2rem

  table
    width: 100%

  th:not(:last-of-type)
    border-right: 1px solid #fcfaf9

  h2
    margin-top: 100px

.Details
  th:last-of-type
    width: 70%

  i:nth-of-type(even)
    color: red

</style>
