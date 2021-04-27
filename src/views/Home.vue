<template>
  <UserList 
    class="container table"
  />
</template>

<script>
export default {
  name: 'Home',
  components: {
    UserList: () => import('@/components/UserList.vue')
  }
}
</script>
<style lang="scss">
 .table {
   margin-top: 10em;
 }
</style>