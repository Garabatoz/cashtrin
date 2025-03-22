<template>
    <main>
      <p>{{ labelVisual }}</p>
      <div>
        <h1 :style="{ color: amountColor }">{{ amountCurrency }}</h1>      
      </div>
      <div class="graphic">
        <slot name="graphic"></slot>
      </div>
      <div class="action">
        <slot name="action"></slot>
      </div>
    </main>
</template>
<script>
const currencyFormater = new Intl.NumberFormat(("es-CO"), {
  style: "currency", currency: "COP"
})

  export default {
    props:{
      label:{
        type: String,
        default: null,
      },
      totalLabel:{
        type: String,
      },
      totalAmount:{
        type:Number,
      },
      amount:{
        type: Number,
        default: null,
      },
    },
    computed: {
      amountVisual(){
        return this.amount !== null ? this.amount : this.totalAmount;
      },
      labelVisual(){
        return this.label !== null ? this.label : this.totalLabel;
      },
      amountColor() {
        return this.amountVisual < 0 ? 'red' : 'var(--brand-green)';
      },
      amountCurrency(){
        return currencyFormater.format(this.amountVisual);
      }      
    },
  }
</script>
<style scoped>
main {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    width: 100%;
  }
  
  h1,
  p {
    margin: 0;
    text-align: center;
  }
  
  h1 {
    margin-top: 14px;
  }
  
  .graphic {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    padding: 48px 24px;
    box-sizing: border-box;
  }
</style>