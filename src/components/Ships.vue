<template>
  <v-container
      text-xs-center fluid grid-list-lg dark
  >
    <v-layout align-content-space-between wrap v-if="this.ships != undefined  " > 
    <v-flex xs12 sm6 md4 lg3  xl2
        v-for="(next, i) in ships"
            :key="i">  
            <ShipCard :shipDetails="next" ></ShipCard>
          
    </v-flex>
     
    </v-layout>
  </v-container>
</template>

<script>
    import axios from 'axios'; 
 
    import ShipCard from '../components/ShipCard.vue' ;
  export default {
        components: {
            ShipCard
        },

    data: () => ({
      ships:[]
      
    }),
    methods: {
        processSWRespone : function(response)  {

            this.ships.push.apply(this.ships,response.results);
           
            if(this.ships.next =! null)
            {
                this.getStarshipBatch(response.next);
            }
              
 
        },
        getStarshipBatch: function(url)  
        {
            axios
                .get(url)
                .then(response => (this.processSWRespone (response.data)));
                
        }
         


    },
      mounted () {
          this.getStarshipBatch('https://swapi.co/api/starships'); 
  }

    
  }
</script>

<style>

</style>