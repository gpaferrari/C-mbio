<template>
    <div id="conversor">

        <h1><b> Câmbio</b></h1>
        <div class="container">
            <div class="container-one">
                <select class="form-select form-select-lg mb-3" aria-label=".form-select-lg example" name="moeda-um" id="moeda-um" @change="calculo()" v-model="moedaUm">
                    <option value="AED">AED</option>
                    <option value="ARS">ARS</option>
                    <option value="AUD">AUD</option>
                    <option value="BGN">BGN</option>
                    <option value="BRL">BRL</option>
                    <option value="BSD">BSD</option>
                    <option value="CAD">CAD</option>
                    <option value="CHF">CHF</option>
                    <option value="CLP">CLP</option>
                    <option value="CNY">CNY</option>
                    <option value="COP">COP</option>
                    <option value="CZK">CZK</option>
                    <option value="DKK">DKK</option>
                    <option value="DOP">DOP</option>
                    <option value="EGP">EGP</option>
                    <option value="EUR">EUR</option>
                    <option value="FJD">FJD</option>
                    <option value="GBP">GBP</option>
                    <option value="GTQ">GTQ</option>
                    <option value="HKD">HKD</option>
                    <option value="HRK">HRK</option>
                    <option value="HUF">HUF</option>
                    <option value="IDR">IDR</option>
                    <option value="ILS">ILS</option>
                    <option value="INR">INR</option>
                    <option value="ISK">ISK</option>
                    <option value="JPY">JPY</option>
                    <option value="KRW">KRW</option>
                    <option value="KZT">KZT</option>
                    <option value="MXN">MXN</option>
                    <option value="MYR">MYR</option>
                    <option value="NOK">NOK</option>
                    <option value="NZD">NZD</option>
                    <option value="PAB">PAB</option>
                    <option value="PEN">PEN</option>
                    <option value="PHP">PHP</option>
                    <option value="PKR">PKR</option>
                    <option value="PLN">PLN</option>
                    <option value="PYG">PYG</option>
                    <option value="RON">RON</option>
                    <option value="RUB">RUB</option>
                    <option value="SAR">SAR</option>
                    <option value="SEK">SEK</option>
                    <option value="SGD">SGD</option>
                    <option value="THB">THB</option>
                    <option value="TRY">TRY</option>
                    <option value="TWD">TWD</option>
                    <option value="UAH">UAH</option>
                    <option value="USD">USD</option>
                    <option value="UYU">UYU</option>
                    <option value="VND">VND</option>
                    <option value="ZAR">ZAR</option>
                </select>
                <input type="text" name="input-um" id="input-um" v-model="quantiaUm" @input="calculo()" />
            </div>
            <button type="button" class="btn btn-info" @click="trocaValor()"><i class="bi bi-arrow-left-right"></i></button>
            <div class="container-two">
                <select class="form-select form-select-lg mb-3" aria-label=".form-select-lg example" id="moeda-dois" @change="calculo()" v-model="moedaDois">
                    <option value="AED">AED</option>
                    <option value="ARS">ARS</option>
                    <option value="AUD">AUD</option>
                    <option value="BGN">BGN</option>
                    <option value="BRL">BRL</option>
                    <option value="BSD">BSD</option>
                    <option value="CAD">CAD</option>
                    <option value="CHF">CHF</option>
                    <option value="CLP">CLP</option>
                    <option value="CNY">CNY</option>
                    <option value="COP">COP</option>
                    <option value="CZK">CZK</option>
                    <option value="DKK">DKK</option>
                    <option value="DOP">DOP</option>
                    <option value="EGP">EGP</option>
                    <option value="EUR">EUR</option>
                    <option value="FJD">FJD</option>
                    <option value="GBP">GBP</option>
                    <option value="GTQ">GTQ</option>
                    <option value="HKD">HKD</option>
                    <option value="HRK">HRK</option>
                    <option value="HUF">HUF</option>
                    <option value="IDR">IDR</option>
                    <option value="ILS">ILS</option>
                    <option value="INR">INR</option>
                    <option value="ISK">ISK</option>
                    <option value="JPY">JPY</option>
                    <option value="KRW">KRW</option>
                    <option value="KZT">KZT</option>
                    <option value="MXN">MXN</option>
                    <option value="MYR">MYR</option>
                    <option value="NOK">NOK</option>
                    <option value="NZD">NZD</option>
                    <option value="PAB">PAB</option>
                    <option value="PEN">PEN</option>
                    <option value="PHP">PHP</option>
                    <option value="PKR">PKR</option>
                    <option value="PLN">PLN</option>
                    <option value="PYG">PYG</option>
                    <option value="RON">RON</option>
                    <option value="RUB">RUB</option>
                    <option value="SAR">SAR</option>
                    <option value="SEK">SEK</option>
                    <option value="SGD">SGD</option>
                    <option value="THB">THB</option>
                    <option value="TRY">TRY</option>
                    <option value="TWD">TWD</option>
                    <option value="UAH">UAH</option>
                    <option value="USD">USD</option>
                    <option value="UYU">UYU</option>
                    <option value="VND">VND</option>
                    <option value="ZAR">ZAR</option>
                </select>

                <input type="text" id="quantia-dois" placeholder="0" v-model="quantiaDois" disabled />
                <p id="ultimaAtualizacao">{{ date }}</p>
            </div>
            
            
        </div>  
        <ConversorDatas :moedaUm="moedaUm" :moedaDois="moedaDois"  />  
    </div>
    
    <Garfico :quantiaDois="quantiaDois" :quantiaUm = "quantiaUm"/>
    

</template>

<script>
import ConversorDatas from "./conversorDatas.vue";
import Garfico from "./garfico.vue";
export default {
    components: { ConversorDatas, Garfico },
    data() {
        return {
            data: [],
            moedaUm: "USD",
            moedaDois: "BRL",
            quantiaUm: 1,
            quantiaDois: 0,
            date: ""
        };
    },

    methods: {
        calculo() {
            fetch(
                `https://api.exchangerate.host/convert?from=${this.moedaUm
                }&to=${this.moedaDois}`
            )
                .then((res) => res.json())
                .then((data) => {
                    this.quantiaDois = (data.result * this.quantiaUm).toFixed(2)
                    this.date = data.date

                });
        },
        trocaValor() {
            const guarda = this.moedaUm;
            this.moedaUm = this.moedaDois;
            this.moedaDois = guarda;
            this.calculo();
        },
    },
    mounted() {
        this.calculo();
    },



};

</script>

<style scoped>
.container {
    display: grid;
    grid-template-columns: auto auto auto;

}

.btn {
    margin: auto;
}
#input-um{
    border-radius: 5px;
    border: solid rgba(171, 171, 248, 0.932);
}
#input-um:hover{
    border: solid whitesmoke;
}
#quantia-dois{
    border-radius: 5px;
    border: solid whitesmoke;
    background-color: white;
    
}

h1{
    color: #34e7e4;
}

p{
    color: white;
}

</style>
