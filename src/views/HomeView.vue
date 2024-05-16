<template>
  <v-app id="home">
    <NavBar />
    <v-container fluid>
      <v-card-title class="card-title">Convertisseur de devises <br> Vérifier les taux de change en temps réel</v-card-title>
      <v-row>

      <v-col cols="12" md="12" class="box">
        <v-card class="currency-card">
          <v-card-text>
            <!-- Currency Converter Form -->
            <v-form class="currency-form" @submit.prevent="convertCurrency">
              <table class="table-box">
                <thead>
                  <tr class="title-menu">
                      <th colspan="2"><h4 class="title-text">Vous envoyez exactement</h4></th>
                      <th colspan="2"><h4 class="title-text">Récipiendaires Gets</h4></th>
                  </tr>
                  <tr class="amount-menu">
                    <th class="text-fields"><v-text-field v-model="amount" label="Montant à convertir" type="number"></v-text-field></th> 
                    <th class="choix"><v-select v-model="fromCurrency" :items="currencies" label="De la devise"></v-select></th>
                    <th class="text-fields"> <v-text-field v-model="amount" label="Montant à convertir" type="number"></v-text-field></th>
                    <th class="choix"><v-select v-model="toCurrency" :items="currencies" label="Vers la devise"></v-select></th>
                  </tr>
                  <tr class="text-affiche">
                    <th  colspan="2">
                      <h4><v-icon color=#6C6BBD left class="mr-0">fas fa-eur</v-icon>    Frais de virement :  3.80 USD</h4>
                    </th>
                    <th colspan="2">
                      <h4> <v-icon color=#6C6BBD left class="mr-0">fas fa-eur</v-icon>    Arrivée prévue : <span>laundi</span></h4>
                    </th> 
                  </tr>
                    <tr>
                      <th colspan="2"  class="text-affiche"><h4> <v-icon color=#6C6BBD left class="mr-0">fas fa-eur</v-icon>    Montant total à convertir : <span>2296.20  USD</span></h4></th>
                    </tr>
                </thead>
              </table>
              <!-- <table class="table-box">
                  <thead> 
                    <tr class="title-menu">
                      <th ><h4 class="title-text">Vous envoyez exactement</h4></th><th></th>
                      <th><h4 class="title-text">Récipiendaires Gets</h4></th><th></th>
                    </tr>
                    <tr class="amount-menu"> 
                        <th class="text-fields">
                            <v-text-field v-model="amount" label="Montant à convertir" type="number"></v-text-field>
                        </th> 
                        <th>
                            <v-select v-model="fromCurrency" :items="currencies" label="De la devise"></v-select>
                        </th>
                        <th class="text-fields">
                            <v-text-field v-model="amount" label="Montant à convertir" type="number"></v-text-field>
                        </th>
                        <th>
                            <v-select v-model="toCurrency" :items="currencies" label="Vers la devise"></v-select>
                        </th>
                    </tr> 
                    <tr class="text-affiche">
                      <th>
                        <h4><v-icon color=#6C6BBD left class="mr-0">fas fa-eur</v-icon>    Frais de virement :  3.80 USD</h4> 
                      </th>
                      <th></th>
                      <th colspan="2">
                        <h4> <v-icon color=#6C6BBD left class="mr-0">fas fa-eur</v-icon>    Arrivée prévue : <span>laundi</span></h4>
                      </th>
                    </tr>
                    <tr>
                      <th colspan="2" class="text-affiche">
                        <h4> <v-icon color=#6C6BBD left class="mr-0">fas fa-eur</v-icon>    Montant total à convertir : <span>2296.20  USD</span></h4>
                      </th>
                    </tr>
                  </thead>
                </table> -->
              <v-btn class="currency-btn" color=#0a2157 type="submit">Commancez</v-btn>
            </v-form>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
      <!-- <div class="head">

          <v-card-header>
          </v-card-header>
            <div class="box">
              <v-card-content>
                <table class="table-box">
                  <thead> 
                    <tr class="title-menu">
                      <th ><h4 class="title-text">Vous envoyez exactement</h4></th><th></th>
                      
                      <th><h4 class="title-text">Récipiendaires Gets</h4></th><th></th>
                    </tr>
                    <tr class="amount-menu"> 
                        <th class="text-fields">
                            <v-text-field v-model="amount" label="Montant à convertir" type="number"></v-text-field>
                        </th> 
                        <th>
                            <v-select v-model="fromCurrency" :items="currencies" label="De la devise"></v-select>
                        </th>
                        <th class="text-fields">
                            <v-text-field v-model="amount" label="Montant à convertir" type="number"></v-text-field>
                        </th>
                        <th>
                            <v-select v-model="toCurrency" :items="currencies" label="Vers la devise"></v-select>
                        </th>
                    </tr> 
                    <tr class="text-affiche">
                      <th>
                        <h4><v-icon color=#6C6BBD left class="mr-0">fas fa-eur</v-icon>    Frais de virement :  3.80 USD</h4>
                        
                      </th>
                      <th></th>
                      <th>
                        <h4> <v-icon color=#6C6BBD left class="mr-0">fas fa-eur</v-icon>    Arrivée prévue : <span>laundi</span></h4>
                      </th>
                      <th></th>
                    </tr>
                    <tr>
                      <th class="text-affiche">
                        <h4> <v-icon color=#6C6BBD left class="mr-0">fas fa-eur</v-icon>    Montant total à convertir : <span>2296.20  USD</span></h4>
                      </th>
                      <th></th>
                    </tr>
                  </thead>
                  
                </table>
                
                <v-btn class="convert-btn" @click="convert">Convert</v-btn>
              </v-card-content>
              <v-card-actions class="card-actions" v-if="convertedAmount">
                <v-spacer></v-spacer>
                <v-text class="converted-amount" v-html="convertedAmount"></v-text>
              </v-card-actions>
            </div>
        </div>
        <div class="taux">

        </div>
        <div class="devices">

        </div> -->
    </v-container>
  </v-app>
</template>

<script>
import { defineComponent } from 'vue';

// Components
import NavBar from '@/components/NavBar.vue';

export default defineComponent({
  name: 'HomeView',
  data() {
    return {
      items: [

      ]
    }
  },
  methods: {
    // convert() {
    //   // Perform currency conversion logic here
    //   // This will likely involve fetching exchange rates from an API
    //   const rate = 1.2; // Placeholder exchange rate
    //   this.convertedAmount = (this.amount * rate).toFixed(2);
    // },
    convertCurrency() {
      // Implement currency conversion logic
      console.log("Convert", this.amount, this.fromCurrency, "to", this.toCurrency);
    },
    transferMoney() {
      // Implement money transfer logic
      console.log("Transfer", this.transferAmount, this.sendCurrency, "to", this.receiveCurrency);
    }
  },
  components: {
    NavBar
  },
  
});

</script>
<style scoped>
  .v-container {
    padding: 1.8% 0;
  }
  .head {
    position: relative;
    text-align: center;
    padding: 0.8%;
    height: 100%;
    width: 100%;
    color: #E7ECF6
  }
  .head{
    content: " ";
    position: absolute;
    height: 100%;
    width: 100%;
    background: #E7ECF6;
    /* transform: skew(3deg ,3deg); */
  }
  .taux {
    content: " ";
    position: absolute;
    top: 100%;
    height: 100%;
    width: 100%;
    background: #021946;
    /* transform: skew(3deg ,3deg); */
  }
  .devices {
    content: " ";
    position: absolute;
    top: 200%;
    height: 100%;
    width: 100%;
    background: #021946;
    /* transform: skew(3deg ,3deg); */
  }
  .box {
    content: " ";
    justify-items: center;
    position: absolute;
    margin-top: 3.8%;
    margin-left: 10%;
    height: 55%;
    width: 80%;
    background: #0a2157;
    border-radius: 10px;
  }
  .card-title {
  /* Style the card title */
  padding-top: 4%;
  color: #021946;
  font-weight: 500;
  font-size: 2.2rem;
  text-align: center;
  font-weight: bold;

  }
  .box {
  /* Style the entire card component */
  position: absolute;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }
  
 .v-card-content {
  /* Style the card content area */
  padding: 16px;
 }
 .table-box{
  /* justify-items: stretch; */
  padding-left: 5%;
  padding-top: 2%;
  width: 98%;
 }
 .title-menu{
    /* padding: 22px; */
 }

 .title-text {
    text-align: left;
 }
 .text-affiche{
    text-align: left;
    padding-top: 2.2%;
 }
 .amount-menu hr{
  /* display: ruby-base-container; 
  flex-direction: row;
  justify-content: space-between;  */
  /* width: 100%; */

}
.choix{
  /* width: 0%; */
}
.text-fields{
  width: 30%;
}
  .v-text-field {
    /* Style the amount text field */
    /* width: 100%; */

  }
  .v-select {
    /* Style the currency selection dropdown */
    /* padding-left: 0%;
    padding: 0%; */
    width: 180px;
  }
  .currency-btn {
    /* Style the convert button */
    margin-top: 16px;
    background-color: #ffffff; /* Green color */
    color: rgb(37, 19, 104);
  }

  .currency-btn:hover {
    background-color: #e4e7f4; /* Darker green on hover */
  }

  .card-actions {
    /* Style the card actions section */
    /* padding: 8px;
    color: #E7ECF6; */
  }

  .converted-amount {
    /* Style the converted amount text */
    color: #E7ECF6;
    font-weight: bold;
    font-size: 1.1rem;
  }

  /************************************************************* */
  .currency-card {
  margin-bottom: 2%;
}
.currency-form {
  
  margin-top: 2%;
}
.currency-btn {
  margin-top: 50px;
}

</style>
