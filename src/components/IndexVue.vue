<template>
  <div id="app" >
    <b-table striped hover :items="items"></b-table>
<span>{{ greetingMessage }}</span>
  </div>
</template>
<script>
export default {
  props: {
    greetingMessage: String
  }
}
</script>