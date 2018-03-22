<template lang="pug">
  .company
    .company-image
      img(:src="getLogoUrl(company.logo)")
    .company-text
      h2.company-name {{ company.name }}
      p.company-description {{ company.description }}
    .company-links
      .separator
      a.link(:href="getInfoSheetUrl(company.pdf)" target="_blank"): icon(name="file-pdf-o" scale="1.6")
      a.link(:href="company.website" target="_blank"): icon(name="globe" scale="1.6")
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
    .company-image  {
      width: 100%;
      img {
        width: 100%;
        border-radius: 10px 10px 0 0;
      }
    }
    .company-text {
      padding: 0 20px 10px;
      color: #222;
      .company-name {
        text-align: center;
        font-weight: 600;
        font-size: 1.6em;
        color: #111;
      }
      .tags {
        margin-left: -5px;
        margin-right: -5px;
        .tag {
          display: inline-block;
          padding: 5px;
          margin: 5px;
          border-radius: 5px;
          font-size: 0.7em;
          background-color: #eee;
        }
      }
    }
    .company-links {
      text-align: center;
      padding: 10px 15px 15px;
      .separator {
        border-top: 1px solid #ddd;
        margin-bottom: 15px;
      }
      .link, .link:visited {
        margin: 5px;
        color: #b2305b;
        &:hover, :focus {
          color: #870042;
        }
      }
    }
  }
</style>
