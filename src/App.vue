<template>
  <div class="container">
    <orderedList />
  </div>
</template>

<script>

import OrderedList from './components/OrderedList'
export default {
  name: 'App',
  components: {
    orderedList: OrderedList
  }
};
</script>

<style lang="css">

@import url("https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,300;0,400;0,700;1,300;1,400;1,700&display=swap");
* {
  box-sizing: border-box;
}

html {
  font-family: "Roboto";
}

.container {
  padding: 20px;
}
</style>