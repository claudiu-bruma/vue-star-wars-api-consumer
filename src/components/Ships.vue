<template>
  <v-container
      text-xs-center fluid grid-list-lg
  >
    <v-layout align-content-space-between wrap v-if="this.ships != undefined  " > 
    <v-flex xs12 sm12 md6 lg4  
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
      ships:[],
 
      ecosystem: [
        {
          text: 'vuetify-loader',
          href: 'https://github.com/vuetifyjs/vuetify-loader'
        },
        {
          text: 'github',
          href: 'https://github.com/vuetifyjs/vuetify'
        },
        {
          text: 'awesome-vuetify',
          href: 'https://github.com/vuetifyjs/awesome-vuetify'
        }
      ],
      importantLinks: [
        {
          text: 'Documentation',
          href: 'https://vuetifyjs.com'
        },
        {
          text: 'Chat',
          href: 'https://community.vuetifyjs.com'
        },
        {
          text: 'Made with Vuetify',
          href: 'https://madewithvuetifyjs.com'
        },
        {
          text: 'Twitter',
          href: 'https://twitter.com/vuetifyjs'
        },
        {
          text: 'Articles',
          href: 'https://medium.com/vuetify'
        }
      ],
      whatsNext: [
        {
          text: 'Explore components',
          href: 'https://vuetifyjs.com/components/api-explorer'
        },
        {
          text: 'Select a layout',
          href: 'https://vuetifyjs.com/layout/pre-defined'
        },
        {
          text: 'Frequently Asked Questions',
          href: 'https://vuetifyjs.com/getting-started/frequently-asked-questions'
        }

      ],
        axiosResponse : ""
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