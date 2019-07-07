<template>
    <v-card v-if="this.shipDetails != undefined" flat tile
             > 
          <v-img
            :src= this.shipDetails.imageUrl
            aspect-ratio="2.75"
          ></v-img>
  
          <v-card-title primary-title>
            <div>
              <h3 class="headline mb-0">{{ this.shipDetails.name }}</h3>
              <div v-html="this.textDescription">   </div>
            </div>
          </v-card-title>
        <v-divider></v-divider>
          <v-card-actions>
            <v-btn flat color="orange">Share</v-btn>
            <v-btn flat color="orange">Explore</v-btn>
          </v-card-actions>
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
                    `<p>model:${this.shipDetails.model}</p>`+
                    `<p>manufacturer:${this.shipDetails.manufacturer}</p>`+
                    `<p>cost:${this.shipDetails.cost_in_credits}</p>`+
                    `<p>starship class:${this.shipDetails.starship_class}</p>`
        }
    }
}


</script>

<style>

</style>