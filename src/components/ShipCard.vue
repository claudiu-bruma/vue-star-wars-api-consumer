<template>
    <v-card v-if="this.shipDetails != undefined" flat tile dark
             > 
 
          <v-card-title dark primary-title class="card-header-title text-md-center">            
              <h3 class="headline mb-0 text-md-center" >{{ this.shipDetails.name }}</h3>             
        
          </v-card-title> 
          <v-divider></v-divider>

          <v-card-text>
              <div class="text-md-left" v-html="this.textDescription">   </div>
          </v-card-text>
        <v-divider></v-divider>

        </v-card>
</template>

<script>
export default {
    props: 
    {   
        shipDetails:{
            name: String,
            model: String,
            manufacturer: String,
            cost_in_credits: String,
            starship_class: String,
            callback: String,
            imageUrl:String
        }
    },
     computed: {
    // a computed getter
        textDescription: function () {
            return `<p>Name:${this.shipDetails.name}</p>`+
                    `<p>Model:${this.shipDetails.model}</p>`+
                    `<p>Manufacturer:${this.shipDetails.manufacturer}</p>`+
                    `<p>Cost:${this.shipDetails.cost_in_credits}</p>`+
                    `<p>Starship class:${this.shipDetails.starship_class}</p>`
        }
    }
}


</script>

<style  lang="scss">
    .card-header-title{
        text-align: center;
        width: 100%;
        background-color: darkslategrey;
        h3{
            width: 100%;
        }
    }

</style>