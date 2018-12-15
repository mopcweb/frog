<template>
    <div class="Quest Nodata">
        <router-link to="/">Go home</router-link>

        <img :src="img" alt="nodata" />

        <span>Quest not found</span>
        For more information, please contact the developers
    </div>
</template>

<script>
import nodata from '@/assets/nodata.png';

const data = () => ({
  img: nodata
})

export default {
  name: 'quest',
  data: data,
};

</script>

<style scoped lang='sass'>
.Nodata
  height: 100%
  padding: 100px 0

  img
    display: block
    margin: 0 auto

  span
    display: block
    font-size: 1.5rem
    margin: 50px auto 10px
</style>
