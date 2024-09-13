<script>
  import ToolbarContent from "./public/components/tooblar-content.component.vue";
  import FooterContent from "./public/components/footer-content.component.vue";
  import {LaureatesApiService} from "./laureates/services/laureates-api.service.js";
  import {Laureate} from "./laureates/model/laureate.entity.js";
  import LaureateList from "./laureates/components/laureate-list.component.vue";

  export default {
    name: "App",
    components: {LaureateList, FooterContent, ToolbarContent},
    data(){
      return {
        drawerVisible: false,
        laureates: [],
        errors: [],
        laureateApi: new LaureatesApiService()
      }
    },
    methods:{
      buildLaureateList(laureates){
        return laureates.map(laureate =>
          new Laureate(
            laureate.id,
            laureate.firstname,
            laureate.surname,
            laureate.born,
            laureate.died,
            laureate.bornCountry,
            laureate.bornCountryCode,
            laureate.bornCity,
            laureate.diedCountry,
            laureate.diedCountryCode,
            laureate.diedCity,
              laureate.gender,
              laureate.prizes
          )
        );
      },
      getLaureates(){
        this.laureateApi.getLaureates().then((response) => {
          let laureates = response.data.laureates;
          this.laureates = this.buildLaureateList(laureates);
          console.log(this.laureates);
        });
      }
    },
    created(){
      this.getLaureates();
    }
  }
</script>

<template>
  <div>
    <toolbar-content></toolbar-content>
    <div>
      <laureate-list :laureates="laureates"></laureate-list>
    </div>
    <footer-content></footer-content>
  </div>
</template>

<style scoped>
</style>
