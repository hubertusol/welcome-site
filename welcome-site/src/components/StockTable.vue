<template>
  <table>
         <tr>
           <th><div class="info" v-if="obj" :class="{'bear': obj[0]['1d'].price_change_pct <0}">{{obj[0].id}}: {{Math.round(obj[0].price)}}$ {{obj[0]['1d'].price_change_pct}}%
           </div>  </th>
           <th class="sep"> <div class="cur" v-if="usd">USD/PLN: {{usd.data.PLN.value}}</div> </th>
         </tr>
         <tr>
           <th><div class="info" v-if="obj" :class="{'bear': obj[1]['1d'].price_change_pct <0}">{{obj[1].id}}: {{Math.round(obj[1].price)}}$ {{obj[1]['1d'].price_change_pct}}%
           </div> </th>
           <th class="sep"> <div class="cur" v-if="eur">EUR/PLN: {{eur.data.PLN.value}} </div></th>
         </tr>
         <tr>
           <th><div class="info" v-if="obj" :class="{'bear': obj[2]['1d'].price_change_pct <0}">{{obj[2].id}}: {{Math.round(obj[2].price)}}$ {{obj[2]['1d'].price_change_pct}}%
           </div> </th>
           <th class="sep"> <div class="cur" v-if="rub">RUB/USD: {{rub.data.USD.value}} </div> </th>
         </tr>
         <tr>
           <th><div class="info" v-if="obj" :class="{'bear': obj[3]['1d'].price_change_pct <0}">{{obj[3].id}}: {{Math.round(obj[3].price)}}$ {{obj[3]['1d'].price_change_pct}}%
           </div> </th>
           <th class="sep"><div class="cur" v-if="cny">CNY/USD: {{cny.data.USD.value}} </div></th>
         </tr>
       </table>
</template>

<script>
export default {
    data() {
        return {
            cnyapi: 'https://api.currencyapi.com/v3/latest?apikey=Ij0ambsvf43uTcT41jh4HWveL4coWG2IUgNhnHmD&base_currency=CNY',
            rubapi: 'https://api.currencyapi.com/v3/latest?apikey=Ij0ambsvf43uTcT41jh4HWveL4coWG2IUgNhnHmD&base_currency=RUB',
            eurapi: 'https://api.currencyapi.com/v3/latest?apikey=Ij0ambsvf43uTcT41jh4HWveL4coWG2IUgNhnHmD&base_currency=EUR',
            usdapi: 'https://api.currencyapi.com/v3/latest?apikey=Ij0ambsvf43uTcT41jh4HWveL4coWG2IUgNhnHmD',
            cny: null,
            rub: null,
            eur: null,
            usd: null,
            api:'https://api.nomics.com/v1/currencies/ticker?key=0d216407944274a1b89a8f9b98101b7f6951a105&ids=BTC,ETH,SOL,BNB',
            obj: null,
            interval: 0
        }
    },
    mounted() {
        
        this.getStocks()
        this.getCurrency()
        this.interval = setInterval(this.getStocks, 60000)
    },
    beforeUnmount() {
        clearInterval(this.interval)
    },
    methods: {
        getStocks() {
            console.log('Loading stocks...')
            fetch(this.api)
            .then((res) => res.json())
            .then((data) => {
            console.log('Stocks loaded!')
            this.obj=data;

            })
        },
        getCurrency() {
            console.log('Loading USD...')
            fetch(this.usdapi)
            .then((res) => res.json())
            .then((data) => {
            console.log('USD loaded!')
            this.usd=data;
            })
            console.log('Loading EUR...')
            fetch(this.eurapi)
            .then((res) => res.json())
            .then((data) => {
            console.log('EUR loaded!')
            this.eur=data;
            })
            console.log('Loading RUB...')
            fetch(this.rubapi)
            .then((res) => res.json())
            .then((data) => {
            console.log('RUB loaded!')
            this.rub=data;
            })
            console.log('Loading CNY...')
            fetch(this.cnyapi)
            .then((res) => res.json())
            .then((data) => {
            console.log('CNY loaded!')
            this.cny=data;
            })
        }
    }
}
</script>

<style>
img {
    height: 4vh;
    width: 4vh;
}
.info {
    text-align: center;
    color: green;
}
.bear {
    text-align: center;
    color: red;
}

</style>