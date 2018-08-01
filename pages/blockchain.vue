<template>
  <main>
    <input placeholder="data" v-model="amount" />
    <button @click="add">Add</button>
    <div v-for="block in data.chain">
      <h3>{{ block.timestamp }}</h3>
      <pre>{{ pretty(block) }}</pre>
    </div>
  </main>
</template>

<script>
/*
https://medium.com/digital-alchemy-holdings/learn-build-a-javascript-blockchain-part-1-ca61c285821e
*/
import crypto from 'crypto-js/sha256'

class Block {
  constructor (index, timestamp, data, previousHash) {
    this.index = index
    this.timestamp = timestamp
    this.data = data
    this.previousHash = previousHash
    this.hash = this.calculateHash()

    // need more here...
    this.nonce = 0
  }

  calculateHash () {
    return crypto(this.index + this.previousHash + this.timestamp + this.data + this.nonce).toString()
  }

  mineBlock (difficulty) {

  }
}

class Blockchain {
  constructor () {
    this.chain = [this.createGenesis()]
  }

  createGenesis () {
    return new Block(0, new Date(), 'Genesis block', '0')
  }

  latestBlock () {
    return this.chain[this.chain.length - 1]
  }

  addBlock (data) {
    const block = this.latestBlock()
    this.chain.push(new Block(block.index + 1, new Date(), data, block.hash))
  }

  checkValid () {
    for (let i = 1; i < this.chain.length; i++) {
      const currentBlock = this.chain[i]
      const previousBlock = this.chain[i - 1]

      if (
        currentBlock.hash !== currentBlock.calculateHash() ||
        currentBlock.previousHash !== previousBlock.hash
      ) {
        return false
      }
    }

    return true
  }
}

export default {
  data: () => ({
    data: new Blockchain(),
    amount: 5
  }),
  methods: {
    pretty (data) {
      return JSON.stringify(data, null, 2)
    },
    add () {
      const { amount } = this
      this.data.addBlock({ amount })
    }
  }
}
</script>
