<template>
  <div class="footerset">
    <p>
      Tvůrci aplikace:
      <br />Jana Červeňák Gerhartová
      <br />Jana Sekaninová
      <br />
    </p>
    <p>
      Fotografie převzaty z:
      <a href="https://unsplash.com/s/photos/dance">Unsplash</a>
    </p>
    <p>© 2019 v rámci Czechitas: DA WEB</p>
  </div>
</template>

<script>
export default {
  name: "ourfooter",
  components: {}
};
</script>

<style>
.footerset {
  color: white;
  background-color: #280004;
  padding: 15px;
  font-size: small;
}

.footerset a {
  color: white;
  font-weight: normal;
}
</style>