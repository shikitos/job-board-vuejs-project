<template>
  <div>
    <label for="input-text">
      <input id="input-text"
             placeholder="Find a job..."
             type="text"
             v-model="query"
             @keyup.enter="findJob"
      >
    </label>
    <br>
    {{ query }}
    <br>
    <div class="job-area" v-if="typeof jobList.query != 'undefined' ">
      {{ jobList() }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'InputText',
  data() {
    return {
      publisher_id: '',
      url_base: 'https://api.indeed.com/ads/apisearch',
      query: '',
      jobList: {},
    };
  },
  methods: {
    findJob() {
      fetch(`${this.url_base}?publisher=${this.publisher_id}=${this.query}`)
        .then((res) => {
          this.query = '';
          return res.json();
        }).then(this.setResults);
    },
    setResults(results) {
      this.jobList = results;
    },
  },
};
</script>

<style scoped>
#input-text {
  height: 50px;
  width: 500px;
  padding: 5px;
  margin-top: 25px;
  outline: none;
  border: none;
  appearance: none;
  font-size: 20px;
  color: #313131;
  -webkit-box-shadow: 12px 16px 31px -8px rgba(0,0,0,0.78);
  -moz-box-shadow: 12px 16px 31px -8px rgba(0,0,0,0.78);
  box-shadow: 12px 16px 31px -8px rgba(0,0,0,0.78);
}
</style>
