<template>
  <v-app id="home">
    <NavBar />
    <v-container fluid>
      
      <v-row class="head">
          <v-card-title class="card-title">Convertisseur de devises <br> Vérifier les taux de change en temps réel</v-card-title>
        
        <v-col cols="12" md="12"  class="box">
          <v-card class="currency-card" >
            <v-card-text>
              <!-- Currency Converter Form -->
              <v-form class="currency-form" @submit.prevent="convertCurrency">
                <table class="table-box">
                  <thead>
                    <tr>
                        <th colspan="2"  ><h4 class="title-text">Vous envoyez exactement</h4></th>
                        <th colspan="2"><h4 class="title-text">Récipiendaires Gets</h4></th>
                    </tr>
                    <tr class="amount-menu">
                      <th class="text-fields"><v-text-field v-model="amount" label="Montant à convertir" type="number" min="1"></v-text-field></th> 
                      <th><v-select  v-model="fromCurrency" :items="currencies" label="De la devise"></v-select></th>
                      <th class="text-fields"> <v-text-field v-model="amount" label="Montant à convertir" type="number"></v-text-field></th>
                      <th><v-select  v-model="toCurrency" :items="currencies" label="Vers la devise"></v-select></th>
                    </tr>
                    <tr class="text-affiche">
                      <th  colspan="2">
                        <h4><v-icon color=#6C6BBD left class="mr-0">fas fa-eur</v-icon>    Frais de virement : <b> 3.80 USD</b></h4>
                      </th>
                      <th colspan="2">
                        <h4> <v-icon color=#6C6BBD left class="mr-0">fas fa-eur</v-icon>    Arrivée prévue : <b>laundi</b></h4>
                      </th> 
                    </tr>
                      <tr class="text-affiche">
                        <th colspan="4"  class="text-affiches"><h4> <v-icon color=#6C6BBD left class="mr-0">fas fa-eur</v-icon>    Montant total à convertir : <b>2296.20  USD</b></h4></th>
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
      <v-row class="taux">
        <v-col class="taux-title-box">
          <h2 class="taux-title">Les taux de change aujourd'hui</h2>
          <v-select v-model="toCurrency" :items="currencies" label="Vers la devise"></v-select>
        </v-col>
        <v-col cols="12" md="12" class="tchange">
          <v-card >
          </v-card>
          <v-table class="table-change">
            <thead>
              <tr>
                <th><v-img src="../assets/ust.png"></v-img></th>
                <th class="nom-pays" colspan="2">Dollar australien</th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 0.40 % <br><b>USD / AUD</b></h3></th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">Dollar US</th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 0.40 % <br><b>USD / AUD</b></h3></th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">Pound British </th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 0.40 % <br><b>USD / AUD</b></h3></th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">Yuan chinois Renminbi</th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 0.40 % <br><b>USD / AUD</b></h3></th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">Euro</th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 0.40 % <br><b>USD / AUD</b></h3></th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">Riyal Saudi </th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 0.40 % <br><b>USD / AUD</b></h3></th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">Dirham United Arab Emirates</th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 0.40 % <br><b>USD / AUD</b></h3></th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">Dirham marocain</th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 0.40 % <br><b>USD / AUD</b></h3></th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">Dirham marocain</th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 0.40 % <br><b>USD / AUD</b></h3></th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">Dirham marocain</th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 0.40 % <br><b>USD / AUD</b></h3></th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">Dirham marocain</th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 0.40 % <br><b>USD / AUD</b></h3></th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">Dirham marocain</th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 0.40 % <br><b>USD / AUD</b></h3></th>
              </tr>
            </thead>
          </v-table>
        </v-col>

      </v-row>
      <v-row class="devices">

        <v-col class="devices-title-box">
          <h2 class="devices-title">Profils de devises</h2>
        </v-col>
        <v-col cols="12" md="12" class="border-devices">
          <v-card >
          </v-card>
          <v-table class="table-devices">
            <thead class="thead-devices">
              <tr>
                <th><v-img src="../assets/ust.png"></v-img></th>
                <th class="nom-pays" colspan="2">AUD - Dollar australien</th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">USD - Dollar US</th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">GBP - Pound British</th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">MYR - Ringgit de Malaisie </th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">SAR - Riyal Saudi </th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">EUR - Euro</th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">CNY - Yuan chinois Renminbi</th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">BRL - Réal Brésilien</th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">EGP - Jenihea Egyptienne</th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">TND - Dinar Tunisien</th>
              </tr>
            </thead>
          </v-table>
          <v-table class="table-devices">
            <thead>
              <tr>
                <th><v-img src="../assets/ust.png"></v-img></th>
                <th class="nom-pays" colspan="2">Dollar australien</th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">AED - Dirham United Arab Emirates</th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">MAD - Dirham marocain</th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">KWD - Dinar Koweïtien</th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">ZAR - Rand Sud-africain</th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">CAD - Dollar Canadien</th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">JPY - Yen Japonaise</th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">MYR - Ringgit de Malaisie </th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">INR - Roupie indienne </th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">TRY - Lires Turques </th>
              </tr>
              <tr>
                <th>image</th>
                <th class="nom-pays" colspan="2">OMR - Rial Omanais </th>
              </tr>
            </thead>
          </v-table>
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
@media (min-width: 1025px) and (max-width: 1280px)  {
  .v-container {
    padding: 1.8% 0;
    justify-content: auto;
  }
  .head{
    content: " ";
    display: block;
    position: absolute;
    padding: 0.8%;
    color: #E7ECF6;
    height: 100%;
    width: 100%;
    background: #E7ECF6;
    /* transform: skew(3deg ,3deg); */
  }
  .taux {
    content: " ";
    position: absolute;
    display: flex;
    top: 100%;
    height: 120%;
    width: 100%;
    background: #021946;
    /* transform: skew(3deg ,3deg); */
  }
  .devices {
    content: " ";
    position: absolute;
    top: 220%;
    height: 120%;
    width: 100%;
    background: #021946;
    /* transform: skew(3deg ,3deg); */
  }
  .box {
    content: " ";
    justify-items: center;
    position: absolute;
    margin-top: 16.8%;
    margin-left: 10%;
    height: 50%;
    width: 80%;
    background: #0a2157;
    border-radius: 10px;
    box-shadow: 0 2px 4px rgb(0, 18, 74);
  }
  .card-title {
  /* Style the card title */
  position: absolute;
  padding-top: 4%;
  width: 100%;
  color: #021946;
  font-weight: 500;
  font-size: 2.2rem;
  text-align: center;
  font-weight: bold;
  }
  .v-card-content {
  /* Style the card content area */
  padding: 16px;
  }
  .table-box{
    /* justify-items: stretch; */
    justify-items: auto;
    justify-content: center;
    position: relative;
    padding-left: 5%;
    padding-top: 1.2%;
    width: 98%;
  }
  .title-text {
      text-align: left;
      font-size: 0.98rem;
  }
  .text-affiche{
      text-align: left;
      padding-top: 3.8%;
      font-size: 1.25rem;
  }
  .text-affiches{
      text-align: left;
      padding-top: 1.8%;
  }
  .amount-menu hr{
  /* display: ruby-base-container; 
  flex-direction: row;
  justify-content: space-between;  */
  /* width: 100%; */
  }
  .text-fields{
    width: 25%;
  }
  .v-select {
    /* Style the currency selection dropdown */
    /* width: 180px; */
    width: 68%;
  }
  .currency-btn {
    /* Style the convert button */
    margin-top: 12%;
    background-color: #ffffff; /* Green color */
    color: rgb(37, 19, 104);
  }

  .currency-btn:hover {
    background-color: #f2f4e4; /* Darker green on hover */
  }

  .card-actions {
    /* Style the card actions section */
    padding: 12%;
    color: #E7ECF6;
  }

  .converted-amount {
    /* Style the converted amount text */
    color: #E7ECF6;
    font-weight: bold;
    font-size: 1.1rem;
  }
  .currency-card {
  margin-bottom: 2%;
  box-shadow: 0 2px 4px rgb(255, 255, 255);
  }
  .currency-form {
    margin-top: 1.6%;
  }
  .currency-btn {
    margin-top: 5%;
    margin-left: 3%;
  }
  .taux-title-box{
    position: absolute;
    display: flex;
    justify-content: space-evenly;
    top: 13%;
    height: 6%;
    left: 3.2%;
    width: 50%;
    padding: 0px;
    background: #FFEAE3;
    border-radius: 2px;
    box-shadow: 0 1px 2px rgb(248, 249, 201);
    text-align: right;
  }
  
  .taux-title{
    width: 80%;
    text-align: left;
    margin-left: 2em;
    padding-top: 1%;
  }
  .tchange {
    position: absolute;
    display: flex;
    top: 22%;
    left: 3.8%;
    height: 65%;
    width: 94%;
    background: #FFEAE3;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgb(248, 249, 201);
  }
  .table-change {
    width: 100%;
  }
  
  .table-change ,h3{
    position: relative;
    text-align: center  ;
  }
  .nom-pays{
    font-size: 135%;
    font-style: unset;
    font-weight: bold;
    letter-spacing: 0.1em;
  }
  .nom-pays:hover{
    background-color:#E7ECF6;
    letter-spacing: 0.19em;
  }
  .border-devices {
    position: absolute;
    display: flex;
    padding-left: 1.5%;
    top: 31%;
    left: 3.8%;
    height: 65%;
    width: 94%;
    border: #f1f8c6 solid 10%;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgb(248, 249, 201);
  }
  .devices-title-box{
    position: absolute;
    display: flex;
    justify-content: space-evenly;
    top: 26%;
    height: 6%;
    left: 5%;
    width: 20%;
    padding: 0px;
    background: #FFEAE3;
    border-radius: 2px;
    box-shadow: 0 1px 2px rgb(248, 249, 201);
    text-align: right;
  }
  .devices-title {
    position: relative;
    display: flex;
    width: 80%;
    text-align: left;
    margin-left: 2em;
    padding-top: 2.5%;
  }
  .table-devices { 
    display: flex;
    margin: 0.15%;
    margin-top:1.8%;
    width: 80%;
    border-radius: 2px;
    
  }
  .v-img{
    margin-left: 18%;
    width: 60%;
    height: 65%;
    justify-content: right;
    text-align: right;
    border-radius: 15%;
  }
  .v-img:hover{
    width: 65%;
  }
}
 
@media (min-width: 768px) and (max-width: 1024px) {
  .v-container {
    padding: 1% 0;
    justify-content: auto;
  }
  .head{
    content: " ";
    display: block;
    position: absolute;
    color: #E7ECF6;
    height: 100%;
    width: 100%;
    background: #E7ECF6;
    /* transform: skew(3deg ,3deg); */
  }
  .taux {
    content: " ";
    position: absolute;
    display: flex;
    top: 100%;
    height: 120%;
    width: 100%;
    background: #021946;
    /* transform: skew(3deg ,3deg); */
  }
  .devices {
    content: " ";
    position: absolute;
    top: 220%;
    height: 120%;
    width: 100%;
    background: #021946;
    /* transform: skew(3deg ,3deg); */
  }
  .box {
    content: " ";
    justify-items: center;
    position: absolute;
    margin-top: 25%;
    margin-left: 11%;
    height: 48.3%;
    width: 80%;
    background: #0a2157;
    border-radius: 10px;
    box-shadow: 0 2px 4px rgb(0, 18, 74);
  }
  .card-title {
  /* Style the card title */
  position: absolute;
  padding-top: 9.3%;
  width: 100%;
  color: #021946;
  font-weight: 500;
  font-size: 2rem;
  text-align: center;
  font-weight: bold;
  }
  .v-card-content {
  /* Style the card content area */
  padding: 16px;
  }
  .table-box{
    /* justify-items: stretch; */
    
    padding-top: 1%;
    width: 100%;
  }
  .title-text {
      text-align: left;
      font-size: 0.98rem;
      width: 50%;
  }
  .text-affiche{
      text-align: left;
      padding-top: 3%;
      font-size: 1.09rem;
  }
  .text-affiches{
      text-align: left;
      padding-top: 1.8%;
      
  }
  .text-affiches h4{
      width: 100%;
  }
  .amount-menu .v-select{
  /* display: ruby-base-container; 
  flex-direction: row;
  justify-content: space-between; 
  width: 70%; */
  }
  .text-fields{
    width: 23%;
  }
  .select-currency {
    /* Style the currency selection dropdown */
    /* width: 180px; */
    margin-right: 15%;
  }
  .currency-btn {
    /* Style the convert button */
    margin-top: 12%;
    background-color: #ffffff; /* Green color */
    color: rgb(37, 19, 104);
  }

  .currency-btn:hover {
    background-color: #f2f4e4; /* Darker green on hover */
  }

  .card-actions {
    /* Style the card actions section */
    padding: 12%;
    color: #E7ECF6;
  }

  .converted-amount {
    /* Style the converted amount text */
    color: #E7ECF6;
    font-weight: bold;
    font-size: 1rem;
  }
  .currency-card {
  margin-bottom: 2%;
  box-shadow: 0 2px 4px rgb(255, 255, 255);
  }
  .currency-form {
    margin-top: 1.6%;
  }
  .currency-btn {
    margin-top: 3.7%;
    margin-left: 3%;
  }
  .taux-title-box{
    position: absolute;
    display: flex;
    justify-content: space-evenly;
    top: 13%;
    height: 6%;
    left: 3.2%;
    width: 50%;
    padding: 0px;
    background: #FFEAE3;
    border-radius: 2px;
    box-shadow: 0 1px 2px rgb(248, 249, 201);
    text-align: right;
  }
  
  .taux-title{
    width: 80%;
    text-align: left;
    margin-left: 2em;
    padding-top: 1%;
  }
  .tchange {
    position: absolute;
    display: flex;
    top: 22%;
    left: 3.8%;
    height: 65%;
    width: 94%;
    background: #FFEAE3;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgb(248, 249, 201);
  }
  .table-change {
    width: 100%;
  }
  
  .table-change ,h3{
    position: relative;
    text-align: center  ;
  }
  .nom-pays{
    font-size: 135%;
    font-style: unset;
    font-weight: bold;
    letter-spacing: 0.1em;
  }
  .nom-pays:hover{
    background-color:#E7ECF6;
    letter-spacing: 0.19em;
  }
  .border-devices {
    position: absolute;
    display: flex;
    padding-left: 1.5%;
    top: 31%;
    left: 3.8%;
    height: 65%;
    width: 94%;
    border: #f1f8c6 solid 10%;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgb(248, 249, 201);
  }
  .devices-title-box{
    position: absolute;
    display: flex;
    justify-content: space-evenly;
    top: 26%;
    height: 6%;
    left: 5%;
    width: 20%;
    padding: 0px;
    background: #FFEAE3;
    border-radius: 2px;
    box-shadow: 0 1px 2px rgb(248, 249, 201);
    text-align: right;
  }
  .devices-title {
    position: relative;
    display: flex;
    width: 80%;
    text-align: left;
    margin-left: 2em;
    padding-top: 2.5%;
  }
  .table-devices { 
    display: flex;
    margin: 0.15%;
    margin-top:1.8%;
    width: 80%;
    border-radius: 2px;
    
  }
  .v-img{
    margin-left: 18%;
    width: 60%;
    height: 65%;
    justify-content: right;
    text-align: right;
    border-radius: 15%;
  }
  .v-img:hover{
    width: 65%;
  }
}


 

</style>
