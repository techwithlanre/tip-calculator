<template>
    <div class="flex flex-row justify-center">
       <div class="w-[550px] bg-gray-100 rounded-xl p-10 mt-20">
            <div class="text-3xl mb-10">Tip Calculator</div>
            <form>
                <div class="mb-3">
                    <label>Bill Amount</label>
                    <input type="number" v-model="billAmount" class="p-2 w-full mt-1" v-on:keyup="calculateTip">
                </div>
                <div class="mb-3">
                    <label class="flex flex-row justify-between items-center">
                    <span>Tip Percentage</span>
                    <span class="text-xs text-orange-500 bg-orange-50 border border-orange-100 px-3 py-1 text-white rounded-full">{{ tipPercentage }}%</span></label>
                    <input v-model="tipPercentage" type="range" class="p-2 w-full mt-1" @input="calculateTip" min="0">
                </div>
                <div class="mb-3">
                    <label class="flex flex-row justify-between items-center">
                    <span>No of Persons</span>
                    <span class="text-xs text-orange-500 bg-orange-50 border border-orange-100 px-3 py-1 text-white rounded-full">{{ noOfPersons }}</span></label>
                    <input v-model="noOfPersons" type="range" class="p-2 w-full mt-1" @input="calculateTip" step="1" min="1" max="20">
                </div>
                <div class="mb-3">
                    <label>Tip Amount</label>
                    <div class="font-bold w-full mt-1">${{ tipAmount }}</div>
                </div>
                <div class="mb-3">
                    <label>Total Bill</label>
                    <div class="font-bold w-full mt-1">${{ totalBill }}</div>
                </div>
                <div class="mb-3">
                    <label>Tip Pe Person</label>
                    <div class="font-bold w-full mt-1">${{ tipPerPerson }}</div>
                </div>
                <div class="mb-3">
                    <label>Total Per Person</label>
                    <div class="font-bold w-full mt-1">${{ totalPerPerson }}</div>
                </div>
            </form>
       </div>
    </div>
</template>



<script>
    export default  {
        data() {
            return {
                billAmount: 0,
                tipPercentage: 5,
                tipAmount: 0,
                totalBill: 0,
                noOfPersons: 1,
                tipPerPerson: 0,
                totalPerPerson: 0
            }
        },
        
        methods: {
            calculateTip() {
                this.tipAmount = parseFloat(this.billAmount) * (parseFloat(this.tipPercentage) / 100);
                this.totalBill = (parseFloat(this.billAmount) + parseFloat(this.tipAmount)).toFixed(2);
                this.tipPerPerson = (parseFloat(this.tipAmount) / parseFloat(this.noOfPersons)).toFixed(2);
                this.totalPerPerson = (parseFloat(this.totalBill) / parseFloat(this.noOfPersons)).toFixed(2);
            }
        }
    }
</script>