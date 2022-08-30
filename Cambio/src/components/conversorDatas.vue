<template>
    <div @change="selecaoData()">
        <input type="date" id="data" v-model="dateInicio" class="form-control" aria-label="Text input with checkbox">
        <input type="date" id="data" v-model="dateFim" class="form-control" aria-label="Text input with checkbox">

        <b><p  id="valorBase">{{  quantiaUm  }} {{  base  }} = {{  symbols  }} {{  quantiaDois }} </p></b>
        
    </div>

</template>

<script>

export default {
    props: {
        moedaUm: String,
        moedaDois: String,

    },
    data() {

        return {
            data: [],
            dateInicio: "",
            dateFim: "",
            quantiaUm: 1,
            quantiaDois: 0,
            base: "",
            symbols: "",
        };
    },
    methods: {
        selecaoData() {
            fetch(
                `https://api.exchangerate.host/timeseries?start_date=${this.dateInicio}&end_date=${this.dateFim}
                &base=${this.base}&symbols=${this.symbols}&places=2`
            )
                .then((res) => res.json())
                .then((data) => {
                    this.base = this.moedaUm
                    this.symbols = this.moedaDois
                    this.quantiaDois = (data.rates)
                    this.data = data.end_date
                    
                    
                    
                })
                return rates.get("BRL")

        },
        
    },


}
</script>

<style scoped>

.form-control{
    margin: 10px;
}

#valorBase{
    color: white;
    
}

</style>