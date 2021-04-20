<template>
  <div class="block">
 
    <div class="logo-center-wrapper" style="">
      <vh-copy class="copy-button"
      :data="'0x35f67c1d929e106fdff8d1a55226afe15c34dbe2'"
      :label="'Contract Address'"
      :confirm_dialog="'buefy'"
      @copied="copiedData">
      <img class="copy-icon" src="~/@/assets/favicon.png" width="64px" height="64px" style="" alt="$BETA">
      </vh-copy> <vh-copy class="sale-button"
      :data="'0x7D4cd63Fe86f5ebcd9e2E4008610cc33eBc1D0c7'"
      :label="'Sale Address'"
      :confirm_dialog="'buefy'"
      @copied="copiedData">
      <img class="copy-icon" src="~/@/assets/wallet.png" width="32px" height="32px" style="" alt="$BETA">
      </vh-copy>
      <img src="~/@/assets/BETA.svg" width="512px;" class="mt-4" alt="">
      <div class="logo-title"><h1 style="">$BETA</h1></div>

    </div>
    <div class="data-wrapper" style="">
      <div class="data-title" style="">ACCESS THE CONTRACT: </div>
      <div class="data-circles"  style="">
      <a class="circle-module" href="https://www.dextools.io/app/uniswap/pair-explorer/0x4849bb3f7fcad49437f3107a578e063677424302">
          <img width="64px" height="64px" src="~/@/assets/dextools.png" alt="">
          </a>
       <a class="circle-module" href="https://app.uniswap.org/#/swap">
          <img width="64px" height="64px" src="~/@/assets/uniswap.png" alt="">
        </a>
        <a class="circle-module" href="https://etherscan.io/address/0x7D4cd63Fe86f5ebcd9e2E4008610cc33eBc1D0c7">
          <img width="64px" height="64px" src="~/@/assets/etherscan.png" alt="">
        </a>
        <a class="circle-module" href="https://app.uniswap.org/#/add/0x35F67c1D929E106FDfF8D1A55226AFe15c34dbE2/ETH">
          <img width="64px" height="64px" src="~/@/assets/liquidity.png" alt="">
       </a>
        </div>
    </div>

  </div>
</template>

<script>
import { mapState, mapActions } from 'vuex';

export default {
  data() {
    return {
      form: {
        quantity: ''
      },
      modalLoginOpen: false,
      modalMakepotionOpen: false
    };
  },
  computed: {
    ...mapState(['settings']),
    isValid() {
      return parseFloat(this.form.quantity);
    },
    maxStrike() {
      const exchangeRate = this.settings.exchangeRates[this.form.asset];
      return exchangeRate && exchangeRate.usd ? exchangeRate.usd : 1e9;
    }
  },
  methods: {
    
    ...mapActions(['SendDai']),
    handleSubmit() {
      this.SendDai({
        //address: '0xb72027693a5B717B9e28Ea5E12eC59b67c944Df7',
        value: this.form.quantity
      });
    },
    maxStake() {
      this.form.quantity = this.$store.state.settings.balance;
    }
  }
};
</script>
<style scoped>
.hasEffect {
  cursor: pointer;
}
</style>

