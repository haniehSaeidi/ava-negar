<template>
    <div class="card">
        <p class="card-title"> {{ info.title }}</p>
        <b-row>
            <b-col class="p-0">
                <h3 class="text-left">{{ info.value }} </h3>
            </b-col>
            <b-col class="pr-2 d-flex">
                <small class="align-self-center"> {{ info.subtitle }}</small>
            </b-col>
        </b-row>
        <b-form-input id="range-1" v-model="info.value" type="range" :min="info.min" :max="info.max" :step="info.step"></b-form-input>
        <b-row>
            <b-col>
            {{ info.min }}
            </b-col>
            <b-col class="text-left">
            {{ info.max }}
            </b-col>
        </b-row>
    </div>
</template>
<script>
export default {
    props: {
        info:{
            title: '',
            subtitle: '',
            value: '',
            min: '',
            max: '',
            step: ''
        }
    }
}
</script>