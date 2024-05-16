<template>
  <v-app id="home">
    <NavBar />
    <v-container fluid>
        <div class="head">
          <v-card-header>
                <v-card-title class="card-title">Convertisseur de devises <br> Vérifier les taux de change en temps réel</v-card-title>
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
                  </thead>
                  <!-- <tbody> 
                    <tr> 
                      <td>
                      </td> 
                      <td>
                      </td>
                    </tr>
                  </tbody> -->
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

        </div>
    </v-container>
  </v-app>
</template>

<script>
import { defineComponent } from 'vue';

// Components
import NavBar from '@/components/NavBar.vue';

export default defineComponent({
  name: 'HomeView',

  components: {
    NavBar
  },
});
</script>
<style scoped>
  .v-container {
    padding: 26px 0;
  }
  .head {
    position: relative;
    text-align: center;
    padding: 12px;
    margin-bottom: 6px;
    height: 730px;
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
    top: 780px;
    height: 100%;
    width: 100%;
    background: #021946;
    /* transform: skew(3deg ,3deg); */
  }
  .devices {
    content: " ";
    position: absolute;
    top: 1520px;
    height: 100%;
    width: 100%;
    background: #021946;
    /* transform: skew(3deg ,3deg); */
  }
  .box {
    margin-top: 100px;
    margin-left: 160px;
    height: 55%;
    width: 80%;
    background: #031234;
    border-radius: 10px;
  }
  .card-title {
  /* Style the card title */
  padding-top: 4%;
  color: #021946;
  font-weight: 500;
  font-size: 2.2rem;
  }
  .box {
  /* Style the entire card component */
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }
  
 .v-card-content {
  /* Style the card content area */
  padding: 16px;
 }
 .table-box{
  justify-items: stretch;
  padding-left: 92px;
  padding-top: 90px;
  width: 98%;
 }
 .title-menu{
    /* padding: 22px; */
 }
 .title-text {
    text-align: left;
 }
 .amount-menu th {
  display: -ms-inline-grid;
  flex-direction: row;
  justify-content: space-between;
}
.text-fields{
  width: 25%;
}
  .v-text-field {
    /* Style the amount text field */
    width: 100%;

  }
  .v-select {
    /* Style the currency selection dropdown */
    /* margin-top: 2px; */
    width: 60%;
  }

  .convert-btn {
    /* Style the convert button */
    margin-top: 16px;
    background-color: #ffffff; /* Green color */
    color: rgb(37, 19, 104);
  }

  .convert-btn:hover {
    background-color: #e8e8e8; /* Darker green on hover */
  }

  .card-actions {
    /* Style the card actions section */
    padding: 8px;
    color: #E7ECF6;
  }

  .converted-amount {
    /* Style the converted amount text */
    color: #E7ECF6;
    font-weight: bold;
    font-size: 1.1rem;
  }
</style>
