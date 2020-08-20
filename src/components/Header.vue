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
}
.header h1{
  text-align: center;
  font-size: 48px;
  color: #0353a4;
  text-transform: uppercase;
  margin-bottom: 20px;
}
</style>