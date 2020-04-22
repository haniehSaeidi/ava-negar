<template>
    <div class="card price-bg p-4 text-white text-center">
        <span class="p-3"> {{ calculatePrice }} تومان</span>
    </div>
</template>

<script>
export default {
    props: ['syncCallInfo', 'durationInfo', 'callStorage', 'monthSelected'],
    data() {
        return {
            price: ''
        }
    },
    computed: {
        calculatePrice(){
            let syncCall = this.syncCallInfo.value*1000000
            let duration = this.durationInfo.value*24
            let callStorage = this.callStorage.value*1000
            this.price = (syncCall + duration + callStorage)*this.monthSelected
            console.log('hahaha', syncCall)
            return this.price.toLocaleString() + this.price.toString().slice(this.price.toString())
        }
    },
}
</script>