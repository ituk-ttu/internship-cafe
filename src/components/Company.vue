<template lang="pug">
  .company
    .company-image
      img(:src="getLogoUrl(company.logo)")
    .company-text
      h2.company-name {{ company.name }}
      p.company-description {{ company.description }}
    .company-links
      a.link.info-link(:href="getInfoSheetUrl(company.pdf)" target="_blank" v-if="company.pdf != null")
        span Info &nbsp
          icon(name="book")
      a.link.info-link.disabled(v-else disabled)
        span Info &nbsp
          icon(name="book")
      a.link.web-link(:href="company.website" target="_blank"): icon(name="globe")
</template>

<script>
  export default {
    name: 'Company',
    props: ['company'],
    methods: {
      getLogoUrl: function (logoName) {
        return '/static/logos/' + logoName
      },
      getInfoSheetUrl: function (infosheetName) {
        return '/static/infosheets/' + infosheetName
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
  .company {
    border-radius: 10px;
    box-shadow: 0 1px 4px 0 rgba(0, 0, 0, .15);
    width: 100%;
    background-color: #fff;
    .company-image  {
      width: 100%;
      padding-top: 15px;
      img {
        width: calc(100% - 30px);
        border-radius: 7px;
      }
    }
    .company-text {
      padding: 0 30px 10px;
      color: #222;
      .company-name {
        text-align: center;
        font-weight: 600;
        font-size: 1.6em;
        color: #111;
      }
    }
    .company-links {
      text-align: left;
      width: 100%;
      border-radius: 0 0 5px 5px;
      overflow: hidden;
      .link {
        text-transform: uppercase;
        font-weight: bold;
        text-decoration: none;
        display: inline-block;
        padding: 11px 10px 10px;
        text-align: center;
        margin: 10px;
        border-radius: 7px;
        span {
          width: 100%;
        }
        &.info-link {
          color: #DE1D3C;
          border: 1px solid #DE1D3C;
          width: calc(100% - 115px);
          &:hover {
            background-color: #DE1D3C;
            color: #fff;
          }
          &.disabled, &:hover.disabled {
            cursor: not-allowed;
            opacity: 0.5;
            color: #DE1D3C;
            border: 1px solid #DE1D3C;
            background-color: #fff;
          }
        }
        &.web-link {
          color: #272262;
          border: 1px solid #272262;
          width: 40px;
          margin-left: 0;
          &:hover {
            background-color: #272262;
            color: #fff;
          }
        }
      }
    }
  }
</style>
