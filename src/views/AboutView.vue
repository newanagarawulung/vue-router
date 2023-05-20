<template>
  <div>
    <h2>Biodata Diri</h2>
    <div class="biodata-item">
      <span>Nama:</span>
      <span>{{ nama }}</span>
    </div>
    <div class="biodata-item">
      <span>Usia:</span>
      <span>{{ usia }}</span>
    </div>
    <div class="biodata-item">
      <span>Npm:</span>
      <span>{{ npm }}</span>
    </div>
    <div class="biodata-item">
      <span>Email:</span>
      <span>{{ email }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Biodata',
  data() {
    return {
      nama: 'Newa Nagara Wulung',
      usia: 20,
      npm: 213510178,
      email: 'newanagarawulung@student.uir.ac.id',
    };
  },
};
</script>




<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
.biodata {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.biodata-title {
  margin-top: 0;
  margin-bottom: 20px;
  font-size: 24px;
  text-align: center;
}

.biodata-item {
  display: flex;
  justify-content: space-between;
  margin-bottom: 10px;
}

.biodata-label {
  font-weight: bold;
}

.biodata-value {
  color: #333;
}
</style>
