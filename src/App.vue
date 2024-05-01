<template>
  <div>
    <nav class="navbar bg-body-tertiary">
      <div class="container-fluid">
        <a class="navbar-brand" href="#">Home</a>
      </div>
    </nav>
    <div class="container-fluid">
      <div class="row">
        <div class="col-lg-5">
          <div class="mb-3">
            <label for="inputJson" class="form-label">Input JSON</label>
            <textarea v-model="inputJson" class="form-control h-100" id="inputJson" rows="40"></textarea>
          </div>
        </div>
        <div class="col-lg-1 d-flex align-items-center justify-content-center">
          <button @click="formatJson" class="btn btn-primary">Format JSON</button>
        </div>
        <div class="col-lg-6">
          <div class="mb-3" style="overflow-x: auto;">
            <label for="outputJson" class="form-label">Formatted JSON</label>
            <pre>{{ formattedJson }}</pre>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputJson: '',
      formattedJson: '',
    };
  },
  methods: {
    formatJson() {
      try {
        const parsedJson = JSON.parse(this.inputJson);
        this.formattedJson = JSON.stringify(parsedJson, null, 2);
      } catch (error) {
        console.error('Invalid JSON format:', error.message);
        this.formattedJson = 'Invalid JSON format';
      }
    },
  },
};
</script>

<style scoped>
/* Styling specific to this component */
</style>
