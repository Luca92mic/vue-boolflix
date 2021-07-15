<template>
  <header>
      <div class="container">
          <div class="logo h1 my-2 font-weight-bold">
              Boolflix
          </div>
          <input class="my-3 fs-2 p-3" 
          type="text"
          placeholder="Search Movies..."
          v-model="searchText"
          @keyup="$emit('ricerca',searchText)">
      </div>
  </header>
</template>

<script>
export default {
    name: "Header",
    data() {
        return {
            searchText: ''
        }
    }
};
</script>