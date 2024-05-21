<template>
  <v-app id="home">
    <NavBar />
    <v-container fluid>
      
      <v-row class="head">
          <v-card-title class="card-title">Convertisseur de devises <br> Vérifier les taux de change en temps réel</v-card-title>
        
        <v-col cols="12" md="12"  class="box">
              <!-- Currency Converter Form -->
              <v-form class="currency-form" @submit.prevent="convertCurrency">
                <v-row class="table-boxs">
                  <div cols="12" md="12" class="table-boxes">
                    <v-col cols="12" md="12" class="table-box1"><h4 class="title-text">Vous envoyez exactement</h4></v-col>
                    <v-col cols="12" md="12" class="table-box2">
                      <v-text-field v-model="amount" label="Montant à convertir" type="number" min="1"></v-text-field>
                      <v-select  v-model="fromCurrency" :items="currencies" label="De la devise"></v-select>
                    </v-col>
                    <v-col cols="12" md="12" class="text-affiche1">
                      <v-icon color=#6C6BBD left class="mr-0">fas fa-eur</v-icon> 
                        <h4> Frais de virement : <b> 3.80 USD</b></h4>
                      </v-col>
                    <v-col class="text-affiche3">
                      <v-icon color=#6C6BBD left class="mr-0">fas fa-eur</v-icon> 
                    <h4>    Montant total à convertir : <b>2296.20  USD</b></h4>
                  </v-col>
                </div>
                  <div cols="12" md="12" class="table-box">
                      <v-col cols="12" md="12" class="table-box3"><h4 class="title-text">Récipiendaires Gets</h4></v-col>
                      <v-col cols="12" md="12" class="table-box4">
                        <v-text-field v-model="amount" label="Montant à convertir" type="number"></v-text-field>
                        <v-select  v-model="toCurrency" :items="currencies" label="Vers la devise"></v-select>
                      </v-col>
                      
                      <v-col cols="12" md="20" class="text-affiche2">

                        <v-icon color=#6C6BBD left class="mr-0">fas fa-eur</v-icon> 
                        <h4>    Arrivée prévue : <b>laundi</b></h4>
                      </v-col>
                  </div>
                </v-row>

                <!-- <table class="table-box">
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
                </table> -->
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
                <v-btn class="currency-btn" type="submit">Commancez</v-btn>
              </v-form>
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
                <th class="flag-pays"><v-img src="../assets/ust.png"></v-img></th>
                <th class="nom-pays" colspan="2">Dollar australien</th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 0.40 % <br><b>USD / AUD</b></h3></th>
              </tr>
              <tr>
                <th class="flag-pays"><v-img src="../assets/ust.png"></v-img></th>
                <th class="nom-pays" colspan="2">Dollar US</th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 0.40 % <br><b>USD / AUD</b></h3></th>
              </tr>
              <tr>
                <th class="flag-pays"><v-img src="../assets/ust.png"></v-img></th>
                <th class="nom-pays" colspan="2">Pound British </th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 0.40 % <br><b>USD / AUD</b></h3></th>
              </tr>
              <tr>
                <th class="flag-pays"><v-img src="../assets/ust.png"></v-img></th>
                <th class="nom-pays" colspan="2">Yuan chinois Renminbi</th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 0.40 % <br><b>USD / AUD</b></h3></th>
              </tr>
              <tr>
                <th class="flag-pays"><v-img src="../assets/ust.png"></v-img></th>
                <th class="nom-pays" colspan="2">Euro</th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 0.40 % <br><b>USD / AUD</b></h3></th>
              </tr>
              <tr>
                <th class="flag-pays"><v-img src="../assets/ust.png"></v-img></th>
                <th class="nom-pays" colspan="2">Riyal Saudi </th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 0.40 % <br><b>USD / AUD</b></h3></th>
              </tr>
              <tr>
                <th class="flag-pays"><v-img src="../assets/ust.png"></v-img></th>
                <th class="nom-pays" colspan="2">Dirham United Arab Emirates</th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 0.40 % <br><b>USD / AUD</b></h3></th>
              </tr>
              <tr>
                <th class="flag-pays"><v-img src="../assets/ust.png"></v-img></th>
                <th class="nom-pays" colspan="2">Dirham marocain</th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 0.40 % <br><b>USD / AUD</b></h3></th>
              </tr>
              <tr>
                <th class="flag-pays"><v-img src="../assets/ust.png"></v-img></th>
                <th class="nom-pays" colspan="2">Dirham marocain</th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 0.40 % <br><b>USD / AUD</b></h3></th>
              </tr>
              <tr>
                <th class="flag-pays"><v-img src="../assets/ust.png"></v-img></th>
                <th class="nom-pays" colspan="2">Dirham marocain</th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 0.40 % <br><b>USD / AUD</b></h3></th>
              </tr>
              <tr>
                <th class="flag-pays"><v-img src="../assets/ust.png"></v-img></th>
                <th class="nom-pays" colspan="2">Dirham marocain</th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 1.5087 <br><b>USD / AUD</b></h3></th>
                <th><h3> 0.40 % <br><b>USD / AUD</b></h3></th>
              </tr>
              <tr>
                <th class="flag-pays"><v-img src="../assets/ust.png"></v-img></th>
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
          <v-table class="table-device">
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
      amount: null,
      recipientAmount: null,
      fromCurrency: null,
      toCurrency: null,
      currencies: ["USD", "EUR", "GBP", "JPY"], // Example currencies
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
@media (min-width: 1281px){
  .v-container {
    padding: 1.8% 0;
  }
  .head{
    content: " ";
    display: flex;
    position: absolute;
    padding: 0.8%;
    color: #E7ECF6;
    height: 960px;
    width: 100%;
    background: #E7ECF6;
  }
  .taux {
    content: " ";
    position: absolute;
    display: flex;
    top: 960px ;
    height:  980px;
    width: 100%;
    background: #021946;
    /* transform: skew(3deg ,3deg); */
  }
  .devices {
    content: " ";
    position: absolute;
    top: 1720px;
    height:  980px;
    width: 100%;
    background: #021946;
    /* transform: skew(3deg ,3deg); */
  }
  .box {
    content: " ";
    display: grid;
    position: absolute;
    margin-top: 24%;
    margin-left: 5.2%;
    height: 490px;
    width: 90%;
    background: #0a2157;
    border: #ffffff solid 7px;
    border-radius: 10px;
    box-shadow: 0 2px 4px rgb(123, 128, 141);
  }
  .card-title {
  /* Style the card title */
    position: absolute;
    padding-top: 7%;
    width: 100%;
    color: #021946;
    font-size: 3.5em;
    text-align: center;
    font-weight: bold;
  }
  
  .table-boxs{
    /* display: flex; */
    padding-left: 3.2%;
    padding-top: 3.5%;
    width: 98%;
  }
  

  .title-text {
      text-align: left;
      font-size: 1.8rem;
  }
  .text-affiche{
      text-align: left;
      padding-top: 1%;
      margin-left: 2%;
      font-size: 120%;
  }
  .v-select {
    width: 20%;
  }
/************************************************************************************************ */
.table-boxs {
  padding-top: 2%;
  padding-left: 4%;
}
.table-box{
    width: 50%;
}
.table-boxes{
    width: 50%;
}
.table-box1 ,.table-box2{
    display: flex;
    padding: 0px;
    width: 100%;
  }
  .table-box3 ,.table-box4{
    display: flex;
    padding: 0px 0px 0px 0px;
    padding-left: 5%;
    width: 100%;
  }
.title-text {
      text-align: left;
      padding-top: 2%;
      margin-left: 2%;
      font-size: 120%;
      font-weight: normal;
}
.v-icon {
  padding-top: 2%;
}
.text-affiche3,
.text-affiche1,
.text-affiche2 {
      display: flex;
      text-align: left;
      padding-top: 6%;
      font-size: 142%;
      padding: 0px 0px 0px 0px;
      margin-top:10px;
}
.text-affiche2{
    margin-left:25px;
}
.text-affiche3{
    margin-top:20px;
}
.text-affiche3 h4,
.text-affiche1 h4,
.text-affiche2 h4 {
      padding-top: 2%;
      padding-left: 1.7%; 
      font-size: 120.5%;
      font-weight: normal;
}
.v-text-field,
.v-select {
  margin-top: 0.5rem;
}
.v-select{
  width: 60%;
}
  .currency-form {
    margin-top: 1%;
  }
  .currency-btn {
    margin-top: 8%;
    margin-left: 80%;
    background-color: #ffffff; /* Green color */
    color: rgb(23, 0, 113);
    width: 16%;
    height: 12%;
    font-size: 150%;
    /* font-weight: lighter; */
    /* font-family: 'Helvetica', Arial, Helvetica, sans-serif;  */
  }
  .currency-btn:hover {
    background-color: #bfc4cd; /* Darker green on hover */
  }
  .taux-title-box{
    position: absolute;
    display: flex;
    justify-content: space-evenly;
    top: 13%;
    height: 47px;
    left: 3.2%;
    width: 70%;
    padding: 0px;
    background: #FFEAE3;
    border-radius: 2px;
    box-shadow: 0 1px 2px rgb(248, 249, 201);
    text-align: right;
  }
  
  .taux-title{
    width: 57%;
    text-align: left;
    margin-left: 2%;
    padding-top: 1%;
    font-size: 153%;
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
  
  .table-change h3{
    position: relative;
    text-align: center  ;
    font-size: 90%;
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
    font-size: 90%;
  }
  .border-devices {
    position: absolute;
    display: flex;
    padding-left: 1.5%;
    top: 19.5%;
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
    top: 15%;
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
    display: flex;
    width: 95%;
    text-align: left;
    margin-left: 2%;
    padding-top: 3%;
    font-size: 149%;
  }
  .table-devices { 
    display: flex;
    margin: 0.15%;
    margin-top:1.8%;
    width: 80%;
    border-radius: 2px;
  }
  .table-device { 
    display: flex;
    margin: 0.15%;
    margin-top:1.8%;
    width: 80%;
    border-radius: 2px;
  }
  .v-img{
    margin-left: 18%;
    width: 95%;
    height: 120%;
    justify-content: right;
    text-align: right;
    border-radius: 15%;
  }
  .v-img:hover{
    width: 105%;
  }
}



























/************************************************************************************************ */
@media (min-width: 1025px) and (max-width: 1280px){
.v-container {
    padding: 1.8% 0;
  }
  .head{
    content: " ";
    display: flex;
    position: absolute;
    padding: 0.8%;
    color: #E7ECF6;
    height: 760px;
    width: 100%;
    background: #E7ECF6;
  }
  .taux {
    content: " ";
    position: absolute;
    display: flex;
    top: 760px ;
    height:  780px;
    width: 100%;
    background: #021946;
    /* transform: skew(3deg ,3deg); */
  }
  .devices {
    content: " ";
    position: absolute;
    top: 1520px;
    height:  780px;
    width: 100%;
    background: #021946;
    /* transform: skew(3deg ,3deg); */
  }
  .box {
    content: " ";
    display: grid;
    position: absolute;
    margin-top: 18%;
    margin-left: 5.5%;
    height: 390px;
    width: 90%;
    background: #0a2157;
    border: #ffffff solid 7px;
    border-radius: 10px;
    box-shadow: 0 2px 4px rgb(123, 128, 141);
  }
  .card-title {
  /* Style the card title */
    position: absolute;
    padding-top: 6%;
    width: 100%;
    color: #021946;
    font-size: 2.6em;
    text-align: center;
    font-weight: bold;
  }
  
  .table-boxs{
    /* display: flex; */
    padding-left: 3.2%;
    padding-top: 3%;
    width: 98%;
  }
  
  .table-box3 ,.table-box4{
    display: flex;
    padding: 0px;
    padding-left: 5%;
    width: 100%;
  }
  .title-text {
      text-align: left;
      font-size: 0.98rem;
  }
  .text-affiche{
      text-align: left;
      padding-top: 2%;
      margin-left: 5%;
      font-size: 120%;
  }
  .v-select {
    width: 20%;
  }
/************************************************************************************************ */
.table-boxs {
  padding: 1.2%;
  padding-left: 4%;
}
.table-box{
    width: 50%;
}
.table-boxes{
    width: 50%;
}
.table-box1 ,.table-box2{
    display: flex;
    padding: 0px;
    width: 100%;
  }
.title-text {
      text-align: left;
      padding-top: 2%;
      margin-left: 5%;
      font-size: 100%;
      font-weight: normal;
}

.text-affiche3,
.text-affiche1,
.text-affiche2 {
  display: flex;
      text-align: left;
      padding-top: 0.2%;
      margin-left: 1%;
      font-size: 122%;
}
.text-affiche3 h4,
.text-affiche1 h4,
.text-affiche2 h4 {
      padding-top: 1%;
}
.v-text-field,
.v-select {
  margin-bottom: 1rem;
}
.v-select{
  width: 60%;
}


/************************************************************************************************ */
  

  

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
    margin-top: 1%;
  }
  .currency-btn {
    margin-top: 5%;
    margin-left: 3%;
    background-color: #ffffff; /* Green color */
    color: rgb(23, 0, 113);
    width: 16%;
    height: 12%;
    font-size: 100%;
    font-weight: bold;
  }
  .currency-btn:hover {
    background-color: #bfc4cd; /* Darker green on hover */
  }
  .taux-title-box{
    position: absolute;
    display: flex;
    justify-content: space-evenly;
    top: 13%;
    height: 47px;
    left: 3.2%;
    width: 70%;
    padding: 0px;
    background: #FFEAE3;
    border-radius: 2px;
    box-shadow: 0 1px 2px rgb(248, 249, 201);
    text-align: right;
  }
  
  .taux-title{
    width: 57%;
    text-align: left;
    margin-left: 2%;
    padding-top: 1%;
    font-size: 153%;
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
  
  .table-change h3{
    position: relative;
    text-align: center  ;
    font-size: 90%;
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
    font-size: 90%;
  }
  .border-devices {
    position: absolute;
    display: flex;
    padding-left: 1.5%;
    top: 19.5%;
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
    top: 15%;
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
    display: flex;
    width: 95%;
    text-align: left;
    margin-left: 2%;
    padding-top: 3%;
    font-size: 149%;
  }
  .table-devices { 
    display: flex;
    margin: 0.15%;
    margin-top:1.8%;
    width: 80%;
    border-radius: 2px;
  }
  .table-device { 
    display: flex;
    margin: 0.15%;
    margin-top:1.8%;
    width: 80%;
    border-radius: 2px;
  }
  .v-img{
    margin-left: 18%;
    width: 95%;
    height: 120%;
    justify-content: right;
    text-align: right;
    border-radius: 15%;
  }
  .v-img:hover{
    width: 105%;
  }
}
@media (min-width: 767px) and (max-width: 1024px){
  .v-container {
    padding: 1.8% 0;
  }
  .head{
    content: " ";
    display: flex;
    position: absolute;
    padding: 0.8%;
    color: #E7ECF6;
    height: 760px;
    width: 100%;
    background: #E7ECF6;
  }
  .taux {
    content: " ";
    position: absolute;
    display: flex;
    top: 760px ;
    height:  780px;
    width: 100%;
    background: #021946;
    /* transform: skew(3deg ,3deg); */
  }
  .devices {
    content: " ";
    position: absolute;
    top: 1520px;
    height:  780px;
    width: 100%;
    background: #021946;
    /* transform: skew(3deg ,3deg); */
  }
  .box {
    content: " ";
    display: grid;
    position: absolute;
    margin-top: 23%;
    margin-left: 5.5%;
    height: 390px;
    width: 90%;
    background: #0a2157;
    border: #ffffff solid 7px;
    border-radius: 10px;
    box-shadow: 0 2px 4px rgb(123, 128, 141);
  }
  .card-title {
  /* Style the card title */
    position: absolute;
    padding-top: 7%;
    width: 100%;
    color: #021946;
    font-size: 2.2em;
    text-align: center;
    font-weight: bold;
  }
  
  .table-boxs{
    /* display: flex; */
    padding-left: 3.2%;
    padding-top: 3%;
    width: 98%;
  }
  
  .table-box3 ,.table-box4{
    display: flex;
    padding: 0px;
    padding-left: 5%;
    width: 100%;
  }
  .title-text {
      text-align: left;
      font-size: 0.98rem;
  }
  .text-affiche{
      text-align: left;
      padding-top: 2%;
      margin-left: 5%;
      font-size: 120%;
  }
  .v-select {
    width: 20%;
  }
/************************************************************************************************ */
.table-boxs {
  padding: 1.2%;
  padding-left: 4%;
}
.table-box{
    width: 50%;
}
.table-boxes{
    width: 50%;
}
.table-box1 ,.table-box2{
    display: flex;
    padding: 0px;
    width: 100%;
  }
.title-text {
      text-align: left;
      padding-top: 2%;
      margin-left: 5%;
      font-size: 100%;
      font-weight: normal;
}

.text-affiche3,
.text-affiche1,
.text-affiche2 {
  display: flex;
      text-align: left;
      padding-top: 0.2%;
      margin-left: 1%;
      font-size: 122%;
}
.text-affiche3 h4,
.text-affiche1 h4,
.text-affiche2 h4 {
      padding-top: 1%;
}
.v-text-field,
.v-select {
  margin-bottom: 1rem;
}
.v-select{
  width: 60%;
}


/************************************************************************************************ */
  

  

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
    margin-top: 1%;
  }
  .currency-btn {
    margin-top: 5%;
    margin-left: 3%;
    background-color: #ffffff; /* Green color */
    color: rgb(23, 0, 113);
    width: 20%;
    height: 12%;
    font-size: 100%;
    font-weight: bold;
  }
  .currency-btn:hover {
    background-color: #bfc4cd; /* Darker green on hover */
  }
  .taux-title-box{
    position: absolute;
    display: flex;
    justify-content: space-evenly;
    top: 13%;
    height: 47px;
    left: 3.2%;
    width: 70%;
    padding: 0px;
    background: #FFEAE3;
    border-radius: 2px;
    box-shadow: 0 1px 2px rgb(248, 249, 201);
    text-align: right;
  }
  
  .taux-title{
    width: 57%;
    text-align: left;
    margin-left: 2%;
    padding-top: 2%;
    font-size: 115.5%;
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
  
  .table-change h3{
    position: relative;
    text-align: center  ;
    font-size: 90%;
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
    font-size: 90%;
  }
  .border-devices {
    position: absolute;
    display: flex;
    padding-left: 1.5%;
    top: 19.5%;
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
    top: 15%;
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
    display: flex;
    width: 95%;
    text-align: left;
    margin-left: 2%;
    padding-top: 5.5%;
    font-size: 114%;
  }
  .table-devices { 
    display: flex;
    margin: 0.15%;
    margin-top:1.8%;
    width: 80%;
    border-radius: 2px;
  }
  .table-device { 
    display: flex;
    margin: 0.15%;
    margin-top:1.8%;
    width: 80%;
    border-radius: 2px;
  }
  .v-img{
    margin-left: 18%;
    width: 95%;
    height: 120%;
    justify-content: right;
    text-align: right;
    border-radius: 15%;
  }
  .v-img:hover{
    width: 105%;
  }

}
@media (min-width: 481px) and (max-width: 767px) {
  

.v-container {
    padding: 1.8% 0;
  }
  .head{
    content: " ";
    display: flex;
    position: absolute;
    padding: 0.8%;
    color: #E7ECF6;
    height: 650px;
    width: 100%;
    background: #E7ECF6;
  }
  .taux {
    content: " ";
    position: absolute;
    display: flex;
    top: 655px ;
    height:  670px;
    width: 100%;
    background: #021946;
    /* transform: skew(3deg ,3deg); */
  }
  .devices {
    content: " ";
    position: absolute;
    top: 1320px;
    height:  650px;
    width: 100%;
    background: #021946;
    /* transform: skew(3deg ,3deg); */
  }
  .box {
    content: " ";
    display: block;
    position: absolute;
    margin-top: 25%;
    margin-left: 5.5%;
    height: 430px;
    width: 90%;
    background: #0a2157;
    border: #ffffff solid 7px;
    border-radius: 10px;
    box-shadow: 0 2px 4px rgb(123, 128, 141);
  }
  .card-title {
  /* Style the card title */
    position: absolute;
    padding-top: 12%;
    width: 100%;
    color: #021946;
    font-size: 1.3em;
    text-align: center;
    font-weight: bold;
  }
.table-boxs {
  display: flex;
  padding: 1.2%;
  padding-left: 4%;
}
.table-box{
    position: absolute;
    width: 93%;
    margin-top: 96px;
    padding: 0px 0px 0px 0px;
}
.table-boxes{
  position: absolute;
    width: 93%;
    margin-top: 1px;
    padding: 0px 0px 0px 0px;
}
.table-box1 ,.table-box2{
    display: flex;
    padding: 0px;
    width: 100%;
  }
  .table-box3 ,.table-box4{
    display: flex;
    padding: 0px 0px 0px 0px;
    width: 100%;
  }
  .table-box4{
    height: 70px;
  }
.title-text {
      text-align: left;
      padding-top: 2%;
      margin-left: 5%;
      font-size: 100%;
      font-weight: normal;
}
.text-affiche3,
.text-affiche1,
.text-affiche2 {
  display: flex;
      text-align: left;
      font-size: 122%;
      padding: 0px 0px 0px 0px;
}
.text-affiche1{
    width: 230%;
    margin-top: 120px;
}
.text-affiche2{
    width: 230%;
}
.text-affiche3{
    width: 230%;
    margin-top:10px;
}
.text-affiche3 h4,
.text-affiche1 h4,
.text-affiche2 h4 {
      padding-top: 2%;
      padding-left: 1.7%; 
      font-size: 101%;
      font-weight: normal;

}
.v-icon {
  padding-top: 1.2%;
}
.v-text-field,
.v-select {
  margin-bottom: 1rem;
}
.v-select{
  width: 60%;
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
    margin-top: 1%;
  }
  .currency-btn {
    margin-top: 355px;
    margin-left: 62%;
    background-color: #ffffff; /* Green color */
    color: rgb(23, 0, 113);
    width: 38%;
    height: 35px;
    font-size: 1.2rem;
    font-weight: bold;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  }
  .currency-btn:hover {
    background-color: #bfc4cd; /* Darker green on hover */
  }
  .taux-title-box{
    position: absolute;
    display: flex;
    justify-content: space-evenly;
    top: 11%;
    height: 50px;
    left: 3.6%;
    width: 94.3%;
    padding: 0px;
    background: #FFEAE3;
    border-radius: 2px;
    box-shadow: 0 1px 2px rgb(248, 249, 201);
    text-align: right;
  }
  .taux-title-box .v-select{
    width: 10%;
    height: 6px;
  }
  .taux-title{
    width: 57%;
    text-align: left;
    margin-left: 2%;
    padding-top: 2%;
    font-size: 115%;
  }
  .tchange {
    position: absolute;
    display: flex;
    top: 20%;
    left: 3.8%;
    height: 75%;
    width: 94%;
    background: #FFEAE3;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgb(248, 249, 201);
  }
  .table-change {
    width: 100%;
    
  }
 .flag-pays{
    width: 90px;
    padding: 0px 0px 0px 0px;
  }
  .table-change h3{
    position: relative;
    text-align: center  ;
    font-size: 72.7%;
    padding: 0px 0px 0px 0px;
  }
 
  .nom-pays{
    width: 21%;
    font-size: 105%;
    font-style: unset;
    font-weight: bold;
    /* letter-spacing: 0.1em; */
  }
  .nom-pays:hover{
    background-color:#E7ECF6;
    letter-spacing: 0.19em;
    /* font-size: 90%; */
  }
  .border-devices {
    position: absolute;
    display: flex;
    justify-content: center;
    padding-left: 1.5%;
    top: 15%;
    left: 3.8%;
    height: 83%;
    width: 94%;
    border: #f1f8c6 solid 10%;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgb(248, 249, 201);
  }
  .devices-title-box{
    position: absolute;
    display: flex;
    justify-content: space-evenly;
    top: 10%;
    height: 6%;
    left: 5%;
    width: 34%;
    padding: 0px;
    background: #FFEAE3;
    border-radius: 2px;
    box-shadow: 0 1px 2px rgb(248, 249, 201);
    text-align: right;
  }
  .devices-title {
    display: flex;
    width: 100%;
    text-align: left;
    margin-left: 2%;
    padding-top: 5%;
    font-size: 124%;
  }
  .table-devices { 
    display: flex;
    position: absolute;
    margin-top:12.5px;
    margin-left: 1.3%;
    margin-right: 0.4%;
    width: 95.7%;
    border-radius: 4px 4px 0px 0px;
    height: 280px;
  }
  .table-device { 
    display: flex;
    position: relative;
    margin: 0.05%;
    margin-top:293px;
    margin-left: 1%;
    width: 110%;
    border-radius: 0px 0px 4px 4px;
  }
  .table-device th,.table-devices th{
    width: 0.2%;
  }
  .table-device .nom-pays,.table-devices .nom-pays{
    width: 2%;
  }
  .v-img{
    border-radius: 3px;
    padding: 0px 0px 0px 0px;
    width: 80%;
  }
  .v-img:hover{
    width: 100px;
  }
  @media (min-width:481px) {
    .table-devices { 
    display: flex;
    position: absolute;
    margin-top:12.5px;
    margin-left: 1.3%;
    margin-right: 0.4%;
    width: 94.7%;
    border-radius: 4px 4px 0px 0px;
    height: 280px;
  }
  .table-device { 
    display: flex;
    position: relative;
    margin: 0.05%;
    margin-top:293px;
    margin-left: 1%;
    width: 110%;
    border-radius: 0px 0px 4px 4px;
  }
  
  } 
}
 

</style>
