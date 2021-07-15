<template>
  <div class="card">
    <ul>
      <li><strong>Titolo: </strong> {{info.title}} </li>
      <li><strong>Titolo originale: </strong> {{info.original_title}} </li>
      <li><strong>Lingua: </strong> {{info.original_language}} </li>
      <li><strong>Titolo: </strong> {{info.vote_average}} </li>
    </ul>
  </div>
</template>

<script>
export default {
    name: "Card",
    props: ["info"],
    
};
</script>