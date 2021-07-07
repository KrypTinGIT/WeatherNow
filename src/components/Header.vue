<template>
    <div class="header">
        <h2>{{ title }}</h2>
    </div>
</template>

<script>
export default {
  name: 'Header',
  props: {
    title: String
  }
}
</script>

<style lang="scss">
    $main-color: #809682;
    
    .header {
        height: 5em;
        h2{
            color: $main-color;
            font-size: 1.5em;
        }
    }
</style>