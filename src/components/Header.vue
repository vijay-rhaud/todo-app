<template>
    <div class="header">
        <h1>Todo Application</h1>
        {{title}}
    </div>
</template>

<script>
export default {
  props: ['title']
}
</script>

<style scoped>
.header {
  width: 100%;
  margin: 40px 0 48px 0;
}
.header h1{
  text-align: center;
  font-size: 40px;
  color: #0353a4;
  text-transform: uppercase;
  margin: 0;
}
</style>