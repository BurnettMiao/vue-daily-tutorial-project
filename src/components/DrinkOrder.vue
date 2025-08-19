<script setup>
import { ref, computed } from 'vue'

const drinks = ref([
  { id: 1, name: 'Coffee', price: 50 },
  { id: 2, name: 'Latte', price: 60 },
  { id: 3, name: 'Matcha Latte', price: 70 },
  { id: 4, name: 'Black Tea', price: 40 }
])

const cart = ref([])

function addDrink(drink) {
  const existItem = cart.value.find((item) => {
    return item.id === drink.id
  })

  if (existItem) {
    existItem.quantity++
  } else {
    cart.value.push({ ...drink, quantity: 1 })
  }
}

function increment(drink) {
  drink.quantity++
}

function decrement(drink) {
  if (drink.quantity > 1) {
    drink.quantity--
  } else {
    cart.value = cart.value.filter((cartItem) => {
      return cartItem.id !== drink.id
    })
  }
}

const totalQuantity = computed(() => {
  return cart.value.reduce((sum, item) => {
    return sum + item.quantity
  }, 0)
})

const totalPrice = computed(() => {
  return cart.value.reduce((sum, item) => {
    return sum + item.price * item.quantity
  }, 0)
})
</script>

<template>
  <h1>Order Drink</h1>

  <!-- 飲料清單 -->
  <h3>飲料清單</h3>
  <div class="drinks-container">
    <div class="drink-item" v-for="drink in drinks" :key="drink.id">
      <span>{{ drink.name }} - {{ drink.price }}</span>
      <button @click="addDrink(drink)">加入</button>
    </div>
  </div>

  <!-- 訂單明細 -->
  <h3>訂單明細</h3>
  <div class="list-container">
    <div v-if="cart.length === 0">尚未有訂單</div>
    <div v-else>
      <span class="cart-item" v-for="drink in cart" :key="drink.id">
        <span>{{ drink.name }} x {{ drink.quantity }} - {{ drink.price * drink.quantity }}</span>

        <span class="list-btns">
          <button @click="decrement(drink)">-1</button>
          <button @click="increment(drink)">+1</button>
        </span>
      </span>
    </div>
  </div>

  <!-- 訂單摘要 -->
  <h3>訂單摘要</h3>
  <div class="summary">
    <p>
      Total Cups: <span class="summary-cups">{{ totalQuantity }}</span>
    </p>
    <p>
      Total Amount: <span class="summary-price">{{ totalPrice }}</span>
    </p>
  </div>
</template>

<style scoped>
h1 {
  font-weight: bold;
}

.drinks-container {
  display: flex;
  flex-direction: column;
  gap: 8px;
  max-width: 260px;
}

.list-container {
  max-width: 260px;
}

.list-container > div {
  padding: 0;
}

.drink-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1rem;
  padding: 0;
}

.cart-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.list-btns {
  display: flex;
  align-items: center;
  gap: 10px;
}

.summary {
  max-width: 260px;
  font-weight: bold;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.summary-cups,
.summary-price {
  font-weight: bold;
}
</style>
