<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Chucky Jokes</ion-title>
      </ion-toolbar>
    </ion-header>
    
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Blank</ion-title>
        </ion-toolbar>
      </ion-header>

      <ion-grid>
        <ion-row class="ion-justify-content-center">
            <ion-card class="ion-text-center mx-auto" >
              <ion-card-header>
                <ion-card-title>
                    <strong>Get a random joke from Chucky</strong>
                </ion-card-title>
              </ion-card-header>

              <ion-button shape="round" color="primary" @click="getrandomjoke" class="ion-align-items-center">Get Joke</ion-button>


              <div v-if="jokes">              
                <ion-card class="ion-text-center" >
                    <ion-card-content>
                      <strong> {{ jokes.value }}</strong>
                    </ion-card-content>
                </ion-card>
              </div>
              <div v-else>
                <ion-card-content>
                  <p> click button </p>
                </ion-card-content>
              </div>
              


            </ion-card>
        </ion-row>
      </ion-grid>

     
      
          
      <div id="container">
       

      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar, IonCard, IonCardContent, IonGrid, IonRow , IonCardHeader, IonCardTitle, IonButton } from '@ionic/vue';
import { defineComponent } from 'vue';
import axios from 'axios'


export default defineComponent({
  name: 'HomePage',
  components: {
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,
    IonToolbar,
    IonCard,
    IonCardContent,
    IonCardHeader,
    IonCardTitle,
    IonButton,
    IonRow,
    IonGrid
  },
  data() {
    return {
      jokes: null
    };
  },
  mounted() {
    fetch('https://api.chucknorris.io/jokes/random')
    .then(res => res.json())
    .then(data => this.jokes = data)
    .catch(err => console.log(err.message));
  },
  methods: {
    getrandomjoke (){
      // forceRerender() ;{
      //   this.jokes += 1;
      // }
      window.location.reload();
    },
    
    
    // async getData() {
    //   try {
    //     let response = await fetch("https://api.chucknorris.io/jokes/random");
    //     this.jokes = await response.json();
    //     // JSON responses are automatically parsed.
        
    //     console.log(response)
    //   } catch (error) {
    //     console.log(error);
    //   }
    // },

    // getData()
    // {
    //   axios.get('https://api.chucknorris.io/jokes/random')
    //   .then(response =>{
    //     this.jokes=response.data;
    //     console.log(this.jokes)
    //   })
    //   .catch(error=>{
    //     console.log(error)
    //   })
      
      
    // },
    // created() {
    //   this.getData();
    // },
  }
});

function forceRerender() {
throw new Error('Function not implemented.');
}
</script>

<style scoped>
#container {
  text-align: center;
  
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;
  
  color: #8c8c8c;
  
  margin: 0;
}

#container a {
  text-decoration: none;
}

#ion-card {
  display:flex;
  flex-direction:column;
  width: 50%;
}

</style>
