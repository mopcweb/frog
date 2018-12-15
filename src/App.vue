<template>
  <div id="app">
    <link rel="stylesheet"
        href="https://use.fontawesome.com/releases/v5.2.0/css/all.css"
        integrity="sha384-hWVjflwFxL6sNzntih27bfxkr27PmbbK/iSvJ+a4+0owXq79v+lsFkW54bOGbiDQ"
        crossorigin="anonymous">
    <router-view />
  </div>
</template>

<style lang="sass">
/* ------------------------------------------------------------------- */
/*                              Default
/* ------------------------------------------------------------------- */

#app
  font-family: 'Avenir', Helvetica, Arial, sans-serif
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  text-align: center

/* ------------------------------------------------------------------- */
/*                              Body & html
/* ------------------------------------------------------------------- */
$light: #fcfaf9
$dark: #1c1c1c

html, body
  margin: 0
  padding: 0
  width: 100%
  height: 100%

body
  overflow-x: hidden
  color: $dark
  background: $light

  *
    box-sizing: border-box

    &:focus
      outline-color: $dark

/* ------------------------------------------------------------------- */
/*                              Table
/* ------------------------------------------------------------------- */

table
  margin: 0 auto
  max-width: 100%
  border-collapse: collapse
  text-align: center

  caption
    margin: 0
    padding: 0
    font-size: 1.5rem
    height: 50px
    line-height: 50px
    border-bottom: 1px solid $light
    color: $light
    background: $dark

  thead
    color: $light
    background: $dark

  td, th
    width: 100px
    height: 80px
    border: 1px solid $dark

i
  font-size: 1.5rem
  color: green

.fa-times
  color: red

.fa-minus
  color: $dark
</style>
