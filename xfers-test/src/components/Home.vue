<template lang="html">
  <div class="">
    <h1>Welcome</h1>
    <h3>Balance: Rp {{ account.available_balance }}</h3>
    <p>You have successfully created your wallet.</p>
    <p>You can top up your wallet by transferring to the following bank:</p>
    <p>Bank Name: {{ trfInfo.bank_name_full }}</p>
    <p>Account Number: {{ trfInfo.bank_account_no }}</p>
    <p>Unique ID: {{ trfInfo.unique_id }}</p>
  </div>
</template>

<script>
export default {
  data () {
    return {
      account: {},
      trfInfo: {}
    }
  },
  methods: {
    getAccount () {
      var config = {
        headers: {'X-XFERS-USER-API-KEY': 'dibSGFzsfpHJh6z9yNiBAPc5dMB1bzfsX5Rzc5Cz39A'}
      }
      this.axios.get('https://sandbox-id.xfers.com/api/v3/user', config)
      .then(response => {
        this.account = response.data
      })
      .catch(err => console.log(err))
    },
    getTransferInfo () {
      var config = {
        headers: {'X-XFERS-USER-API-KEY': 'dibSGFzsfpHJh6z9yNiBAPc5dMB1bzfsX5Rzc5Cz39A'}
      }
      this.axios.get('https://sandbox-id.xfers.com/api/v3/user/transfer_info', config)
      .then(response => {
        this.trfInfo = response.data
      })
      .catch(err => console.log(err))
    }
  },
  created () {
    this.getAccount()
    this.getTransferInfo()
  }
}
</script>

<style lang="css">
</style>
