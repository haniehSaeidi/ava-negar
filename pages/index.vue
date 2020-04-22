<template>
  <div id="app">
    <div class="header d-flex">
      <h3 class="container header-title text-left text-white align-self-center">
        آوانگار
      </h3>
    </div>
    <div class="container my-5">
      <h2 class="text-right dark-gray">داشبورد من</h2>
      <p class="dark-gray text-right">سامانه جامع آرشیو و نگهداری اسناد و مدارک آوانگار ، قابلیت نگهداری و آرشیو هر نوع مستندی را در خود دارا می باشد و بعلت ساختار فنی بسیار پیشرفته خود، امکان دسترسی ساده و سریع به اسناد را بخوبی مهیا نموده است.</p>
      <b-row class="pr-3">
        <b-col sm="12" md="4" lg="4" class="pr-0 mt-sm-3 mt-xs">
          <rangeSlidePanel :info="syncCallInfo" />
        </b-col>
        <b-col sm="12" md="4" lg="4" class="pr-0 mt-sm-3 mt-xs">
          <rangeSlidePanel :info="durationInfo" />
        </b-col>
        <b-col sm="12" md="4" lg="4" class="pr-0 mt-sm-3 mt-xs">
          <div class="card">
            <div>
              <p class="card-title">انتخاب پنل</p>
              <b-form-group>
                <b-row>
                  <b-col cols="auto" class="pl-0">
                    <b-form-radio v-model="monthSelected" name="some-radios" value="3" />
                  </b-col>
                  <b-col class="pr-2">
                    <span>۳ ماهه</span>
                  </b-col>
                </b-row><b-row>
                  <b-col cols="auto" class="pl-0">
                    <b-form-radio v-model="monthSelected" name="some-radios" value="6" />
                  </b-col>
                  <b-col class="pr-2">
                    <span>۶ ماهه</span>
                  </b-col>
                </b-row>
                <b-row>
                  <b-col cols="auto" class="pl-0">
                    <b-form-radio v-model="monthSelected" name="some-radios" value="10" />
                  </b-col>
                  <b-col class="pr-2">
                    <span>یک ساله</span>
                    <small class="text-orange">دو ماه رایگان</small>
                  </b-col>
                </b-row>
              </b-form-group>
            </div>
          </div>
        </b-col>
      </b-row>
      <b-row class="pr-3">
        <b-col sm="12" md="4" lg="4" class="pr-0 mt-sm-3 mt-xs">
          <rangeSlidePanel :info="callStorage" />
        </b-col>
        <b-col sm="12" md="4" lg="4" class="pr-0 mt-sm-3 mt-xs">
          <rangeSlidePanel :info="storageInfo" />
        </b-col>
        <b-col sm="12" md="4" lg="4" class="pr-0 mt-sm-3 mt-xs">
          <price :syncCallInfo="syncCallInfo"
                 :durationInfo="durationInfo"
                 :callStorage="callStorage"
                 :monthSelected="monthSelected" />
          <div class="card submit-bg p-1 cursor-pointer text-white text-center mt-1">
            پرداخت
          </div>
        </b-col>
      </b-row>
    </div>
  </div>
</template>

<script>
import rangeSlidePanel from '../components/rangeSlidePanel'
import price from '../components/price'

export default {
  components: {
    rangeSlidePanel,
    price
  },
  data () {
    return {
      syncCallInfo: {
        title: 'حداکثر تماس همزمان',
        subtitle: 'تماس',
        value: 100,
        min: 100,
        max: 1000,
        step: 100
      },
      durationInfo: {
        title: 'میزان مکالمه / دقیقه',
        subtitle: 'مکالمه / دقیقه',
        value: 10000,
        min: 10000,
        max: 100000,
        step: 1000
      },
      storageInfo: {
        title: 'میزان حجم دخیره سازی اطلاعات',
        subtitle: 'گیگ',
        value: 1,
        min: 1,
        max: 100,
        step: 1
      },
      callStorage: {
        title: 'میزان نگهداری فایل مکالمه تماس / روز',
        subtitle: '/ در روز',
        value: 1,
        min: 1,
        max: 60,
        step: 1
      },
      monthSelected: 3,
      price: ''
    }
  },
}
</script>

<style>

  html, body {
    text-align: right;
    color: #747474;
    direction: rtl;
    background: #f4f7fc;
    font-family: "IRANSans"
  }

  .header {
    background: rgb(87,62,129);
    background: linear-gradient(90deg, rgba(87,62,129,1) 0%, rgba(141,66,97,1) 35%, rgba(249,157,63,1) 100%);
    height: 50px
  }

  .dark-gray {
    color: #747474;
  }

  .card {
    box-shadow: 0 0.5em 1em -0.125em rgba(10,10,10,.1), 0 0 0 1px rgba(10,10,10,.02);
    border-radius: 10px;
    transition: box-shadow 0.2s ease-in-out;
    padding: 10px
  }

  .card-title {
    font-weight: bold
  }

  .text-orange {
    color: orange
  }

  .price-bg {
    background: #883e64
  }

  .submit-bg {
    background: #6ad029
  }

  .cursor-pointer {
    cursor: pointer;
  }

  @media only screen and (max-width: 600px) {
    .mt-xs {
      margin-top: 1rem;
    }
  }
</style>
