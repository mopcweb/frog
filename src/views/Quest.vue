<template>
  <div v-if="data.length">
    <Data
      v-for='(item, index) of data'
      :key='index'
      :title='location'
      :data="data[index]"
      :pathed="pathed[index]"
      :allleafs="allleafs"
    />
  </div>
  <div v-else>
    <Nodata />
  </div>
</template>

<script>
import Data from '@/components/Data'
import Nodata from '@/components/Nodata'

const data = function() {
  return {
    location: window.location.pathname.replace('/',''),
    data: [],
    allleafs: [],
    pathed: [],
  }
}

function created() {
  fetch('./server/GeneralQuestsInfo.json')
    .then(response => {
      return response.json()
    })
    .then(data => {
      const filtered = data.filter(item => item.alias === this.location);
      this.data = filtered;
    })
    .catch(err => console.log('Error: ' + err.message));

    fetch('./server/FinishedQuestsLeafs.json')
      .then(response => {
        return response.json()
      })
      .then(data => {
        // Filtering whole data for suitable one
        const leafs = this.data.map(item => {
          // New empty array for pushing data
          let leafs = []

          // Checking leaf id matches to quest id
          data.map(leaf => {
            if (item.id === leaf.questId) leafs.push(leaf)
          });

          return leafs
        });

        // Pathed leafs for this quest
        this.pathed = leafs;

        // All leafs
        this.allleafs = data;
      })
      .catch(err => console.log('Error: ' + err.message));
}

export default {
  name: 'quest',
  components: {
    Data,
    Nodata
  },
  data: data,
  created: created,
};

</script>
