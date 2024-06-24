<template>
      <Toast />
      <div v-if="loading" class="overlay">
      <ProgressSpinner />
    </div>
    <section class="p-col-12">
        <div class="p-grid flex justify-content-center align-items-center">
          <div class="p-col-6 text-center">
            <img src="../assets/img/pages/yamuna_auth_logo.png" alt="logo" class="p-shadow-2" />
          </div>
        </div>
      </section>
    <div class="payment-gateway">
      <div class="p-fluid payment-content">
        <div class="p-field">
          <label>Summary</label>
          <p>Product: Name of product</p>
          <p>Price: Rs: 40,000</p>
          <p>
            Lorem ipsum, dolor sit amet consectetur adipisicing elit. Atque
            nihil neque quisquam aut repellendus, dicta vero? Animi dicta !
          </p>
        </div>
        <div class="card mt-3">
    <div class="p-field mb-2">
      <label for="cardNumber">Card Number</label>
      <InputText id="cardNumber" v-model="cardNumber" v-mask="'#### #### #### ####'" />
    </div>
    <div class="p-field mb-2">
      <label for="expiryDate">Expiry Date (MM/YYYY)</label>
      <Calendar id="expiryDate" v-model="expiryDate" class="p-component" dateFormat="mm/yy" showIcon />
    </div>
    <div class="p-field mb-2">
      <label for="cvv">CVV Code</label>
      <InputText id="cvv" v-model="cvv" v-mask="'###'" />
    </div>
    <div class="p-field mb-2">
      <label for="cardName">Name on the Card</label>
      <InputText id="cardName" v-model="cardName" />
    </div>
    <Button label="Make Payment" class="p-button-success mt-2" @click="makePayment" />
  </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'PaymentGateway',
    data() {
      return {
        cardNumber: '',
      expiryDate: null,
      cvv: '',
      cardName: '',
      loading: false 
      };
    },
    methods: {
        async makePayment() {
      if (this.validateInputs()) {
        this.loading = true; // Show loading spinner
        // Simulate a payment process with a timeout
        setTimeout(() => {
          this.loading = false; // Hide loading spinner
          this.$toast.add({ severity: 'success', summary: 'Success', detail: 'Payment Successful', life: 3000 });
        }, 2000); // Simulating a 2-second payment process
      }
    },
    validateInputs() {
      if (this.cardNumber.length !== 16) { // 16 digits + 3 spaces
        this.$toast.add({ severity: 'error', summary: 'Error', detail: 'Card number must be 16 digits long', life: 3000 });
        return false;
      }
      if (this.cvv.length !== 3) {
        this.$toast.add({ severity: 'error', summary: 'Error', detail: 'CVV code must be 3 digits long', life: 3000 });
        return false;
      }
      return true;
    }
    }   
  };
  </script>
  
  <style scoped>
  .payment-gateway {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh; 
    margin-top: -110px;
  }
  
  .payment-content {
    width: 100%;
    max-width: 500px;
    padding: 20px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    border-radius: 8px;
    background-color: #fff;
  }
  
  .text-center {
    text-align: center;
  }

  .overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background: rgba(0, 0, 0, 0.5);
  z-index: 9999;
}
  </style>
  