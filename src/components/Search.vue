<template lang="pug">
  div
    .top-bar
      .left
      .right
    div.container
      h1.title PRAKTIKAKOHVIK
      .companies-wrapper
        p(v-if="companies == null"): icon(name="gear" scale="2" spin)
        masonry.companies(:cols="{default: 4, 1279: 3, 959: 2, 639: 1}", :gutter="30")
          company.company(v-for="company in companies",
          :key="company.name", :company="company")
      p.footer
        span.logo-purple >
        span.logo-black itük
        span.logo-purple _
</template>

<script>
  import company from './Company'

  export default {
    components: {company},
    name: 'Search',
    data () {
      return {
        companies: null
      }
    },
    mounted: function () {
      let self = this
      this.$http.get('/static/companies.json').then((res) => { self.companies = res.body.companies })
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
  .top-bar {
    width: 100%;
    height: 15px;
    .left {
      display: inline-block;
      background-color: #DE1D3C;
      width: 50%;
      height: 100%;
    }
    .right {
      display: inline-block;
      background-color: #262272;
      width: 50%;
      height: 100%;
    }
  }
  .container {
    margin-top: 45px;
    padding: 30px;
    text-align: center;
    .companies-wrapper {
      max-width: 1280px;
      margin-left: auto;
      margin-right: auto;
      .companies {
        .company {
          margin-bottom: 30px;
        }
      }
    }
  }
  .title {
    font-weight: bold;
    font-size: 3em;
    margin-top: 0;
    margin-bottom: 70px;
    color: #000;
  }

  @media screen and (max-width: 480px) {
    .title {
      font-size: 1.8em;
    }
  }
</style>

<style>
  .search-input > .tags-input {
    font-size: 2em;
    padding: 10px;
    text-align: left;
    border-radius: 10px;
    border: 1px solid #eee;
    width: calc(100% - 20px);
    max-width: 1280px;
    margin-left: auto;
    margin-right: auto;
  }
  .search-input {
    margin-bottom: 80px;
  }
  .tags-input span {
    margin-left: 0.3rem;
    background-color: #eee;
    padding: 4px 5px 7px 5px;
    border-radius: 5px;
    font-size: 0.7em;
  }
  .tags-input > input {
    font-size: 1em;
  }
  .typeahead {
    text-align: left;
    margin-bottom: -36px;
  }
  .typeahead > .badge {
    padding: 5px;
    margin: 5px;
    border-radius: 5px;
    font-size: 0.7em;
    background-color: #eee;
  }
  .footer {
    font-weight: bold;
    font-size: 1.2em;
  }
  .logo-purple {
    color: #870042
  }
  .logo-black {
    color: #000
  }
</style>
