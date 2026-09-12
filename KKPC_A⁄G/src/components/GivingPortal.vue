<template>
  <section class="py-20 bg-neutral-900/50">
    <div class="max-w-4xl mx-auto px-4 sm:px-6">
      <div class="text-center mb-12">
        <span class="text-xs uppercase tracking-widest text-amber-500 font-bold">Online Giving</span>
        <h2 class="text-3xl sm:text-4xl font-bold text-white mt-2">Honour the Lord with Your Substance</h2>
        <p class="text-neutral-400 text-sm mt-3">Tithe, First Fruits, Offering, and KKPC A/G Aid Scholarship donations.</p>
      </div>

      <div class="bg-neutral-900 border border-neutral-800 rounded-3xl p-6 sm:p-10 shadow-2xl">
        <!-- Step 1: Category Selection -->
        <div class="mb-8">
          <label class="block text-xs font-bold uppercase tracking-wider text-neutral-400 mb-3">
            Select Giving Purpose
          </label>
          <div class="grid grid-cols-2 sm:grid-cols-3 gap-3">
            <button 
              v-for="cat in categories" 
              :key="cat.id"
              @click="selectedCategory = cat.id"
              :class="selectedCategory === cat.id ? 'border-amber-500 bg-amber-500/10 text-amber-400' : 'border-neutral-800 bg-neutral-800/40 text-neutral-300 hover:border-neutral-700'"
              class="p-3.5 rounded-xl border text-left text-xs font-semibold transition-all"
            >
              <div class="font-bold text-sm">{{ cat.name }}</div>
              <div class="text-[11px] text-neutral-400 mt-1">{{ cat.badge }}</div>
            </button>
          </div>
        </div>

        <!-- Step 2: Currency & Amount -->
        <div class="grid sm:grid-cols-2 gap-4 mb-8">
          <div>
            <label class="block text-xs font-bold uppercase tracking-wider text-neutral-400 mb-2">Currency</label>
            <select v-model="currency" class="w-full bg-neutral-800 border border-neutral-700 rounded-xl px-4 py-3 text-sm text-white focus:outline-none focus:border-amber-500">
              <option value="GHS">GHS - Ghana Cedi (Mobile Money & Cards)</option>
              <option value="USD">USD ($) - US Dollar</option>
              <option value="GBP">GBP (£) - British Pound</option>
              <option value="EUR">EUR (€) - Euro</option>
            </select>
          </div>
          <div>
            <label class="block text-xs font-bold uppercase tracking-wider text-neutral-400 mb-2">Amount</label>
            <div class="relative">
              <input 
                type="number" 
                v-model="amount" 
                placeholder="0.00"
                class="w-full bg-neutral-800 border border-neutral-700 rounded-xl px-4 py-3 text-sm text-white focus:outline-none focus:border-amber-500"
              />
            </div>
          </div>
        </div>

        <!-- Step 3: Payment Method -->
        <div class="mb-8">
          <label class="block text-xs font-bold uppercase tracking-wider text-neutral-400 mb-3">Payment Channel</label>
          <div class="grid grid-cols-2 sm:grid-cols-4 gap-3">
            <button 
              v-for="method in methods" 
              :key="method.id"
              @click="selectedMethod = method.id"
              :class="selectedMethod === method.id ? 'border-amber-500 bg-amber-500/10 text-white' : 'border-neutral-800 bg-neutral-800/40 text-neutral-400'"
              class="p-3 rounded-xl border text-center text-xs font-medium"
            >
              {{ method.name }}
            </button>
          </div>
        </div>

        <!-- Action Button -->
        <button 
          @click="submitGiving"
          class="w-full py-4 rounded-xl bg-gradient-to-r from-amber-500 to-amber-600 hover:from-amber-400 hover:to-amber-500 text-neutral-950 font-bold text-sm uppercase tracking-wider shadow-lg shadow-amber-500/25 transition-all"
        >
          Proceed to Secure Giving ({{ currency }} {{ amount || '0.00' }})
        </button>

        <!-- USSD Code Note -->
        <div class="mt-4 text-center text-xs text-neutral-400">
          In Ghana, dial <span class="text-amber-400 font-bold">*714*33#</span> on all networks to give via USSD.
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const categories = [
  { id: 'tithe', name: 'Tithe', badge: '10% Increase' },
  { id: 'offering', name: 'Offertory', badge: 'Freewill' },
  { id: 'firstfruit', name: 'First Fruits', badge: 'Annual Dedication' },
  { id: 'central-aid', name: 'Central Aid', badge: 'Scholarship Fund' },
  { id: 'project', name: 'Temple Project', badge: 'Expansion' }
]

const methods = [
  { id: 'visa-master-card', name: 'Visa/Master' },
  { id: 'payPal', name: 'payPal' },
  { id: 'cash-app', name: 'Cash App' },
  { id: 'Zelle', name: 'Zelle' }
]

const selectedCategory = ref('tithe')
const currency = ref('USD')
const amount = ref(100)
const selectedMethod = ref('visa-master-card')

const submitGiving = () => {
  alert(`Thank you for honouring the Lord with your ${selectedCategory.toUpperCase()} of ${currency.value} ${amount.value}!`)
}
</script>