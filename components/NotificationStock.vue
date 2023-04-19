<template>
    <div class="masterFlex">
        <div>
            <div v-if="firstThreeItems.length > 0">
                <div v-for="firstThreeItem in firstThreeItems" :key="firstThreeItem.id" class="alert alert-danger">
                    <p>{{ myDate }}</p>
                    <i class="close icon"></i>
                    <div class="header">
                        <h1 class="text-dark fw-bold">{{ firstThreeItem.exchange }}</h1>
                        <p class="text-white fw-bold">{{ firstThreeItem.name }}</p>
                        <p class="text-dark fw-bold">Price : <span class="text-white fw-bold"> {{
                            firstThreeItem.price }} USD</span></p>
                        <p v-if="firstThreeItem.open > firstThreeItem.price"> Today : <img class="image"
                                src="../public/icone/decrease.png" alt=""></p>
                        <p v-else> Today : <img class="image" src="../public/icone/increase.png" alt=""></p>
                    </div>
                    <slot></slot>
                </div>
            </div>
            <div v-else>
                <div class="spinner-border" role="status">
                    <span class="sr-only"></span>
                </div>
            </div>
        </div>
        <div>
            <TheChart2 />
        </div>
    </div>
</template>
  
<script>
export default {
    data() {
        return {
            firstThreeItems: [],
            myDate: new Date()
        }
    },
    mounted() {
        this.updateMyDate();
        fetch('https://financialmodelingprep.com/api/v3/quote/AAPL,GOOG,MMM?apikey=9fb2c7e0767d325798293dbd93d429f3')
            .then(response => response.json())
            .then(data => {
                this.firstThreeItems = data;
                console.log(data)
            })
            .catch(error => {
                console.error('Error:', error);
            });
    },
    methods: {
        updateMyDate() {
            setInterval(() => {
                this.myDate = new Date();
            }, 1000);
        },
    },
};

</script>
  
<style>
.alert {
    max-width: 40%;
    margin-top: 10%;
    margin-left: 10%;
}

.spinner-border {
    margin-top: 5%;
    margin-left: 10%;
}

img {
    max-width: 40px;
}

.masterFlex {
    display: flex;
}
</style>
  