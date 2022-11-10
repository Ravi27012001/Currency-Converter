<script setup lang="ts">
// defining a string for currency name and its value w.r.t INR
 let AllCur = ref<Record<string,[string,number]>>({
  KWD:["Kuwaiti Dinar",0.00378],
  BHD:["Bahaini Dinar",0.00459],
  OR:["Omani Rial",0.0047],
  BPS:["British Pound Sterling",0.01064],
  EE:["European Euro",0.01221],
  USD:["US Dollar",0.01225],
  BRD:["Brunei Dollar",0.01716],
  NZD:["New Zealand Dollar",0.0206],
  AF:["Aruban Florin",0.02194],
  INR:["Indian Rupee",1]

});
  
const c1 = ref<string>('INR');
const c2 = ref<string>("USD");
console.log(c2.value)
const v1 = ref<number>(1);
const v2 = ref<number>(0.012);

function onclickk(){  //function to calculate conversion value
const calculation = v1.value * (AllCur.value[c2.value][1] / AllCur.value[c1.value][1]);
console.log(calculation);
v2.value = calculation;
}
function exchange(){  //function for exchange button
  let t1 = ref(c1.value)
  c1.value = c2.value;
  c2.value = t1.value;

  let t2 = ref(v1.value);
  v1.value = v2.value;
  v2.value = t2.value
} 
</script>

<template>
  <div class="text-center">
    <h1 class="text-[35px] text-center font-serif font-bold mt-16">
      Currency Converter App
    </h1>

    <div class="text-center flex w-96 m-auto gap-2 mt-8">
      <div class="">
        <select
          v-model="c1"
          class="
            border-2 border-black
            text-[25px]
            bg-slate-300
            font-serif font-medium
            w-60
            h-8
          "
        >
        <!-- Putting all options using v-for  -->
          <option v-for="(value, key) in AllCur" :key="key" :value="key"> 
            {{ value[0] }} 
          </option>
          </select
        ><br />
        <input
          v-model="v1"
          type="text"
          name=""
          id=""
          class="
            border-2
            text-blue-700
            border-black
            text-[25px]
            font-serif font-medium
            w-60
            h-8
            p-2
          "
        />
      </div>
      <!-- exchange button for exchanging LHS to RHS -->
      <button @click="exchange()"> 
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke-width="1.5"
          stroke="currentColor"
          class="w-6 h-6"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M7.5 21L3 16.5m0 0L7.5 12M3 16.5h13.5m0-13.5L21 7.5m0 0L16.5 12M21 7.5H7.5"
          />
        </svg>
      </button>

      <div>
        <select
          v-model="c2"
          class="
            border-2 border-black
            text-[25px]
            bg-slate-300
            font-serif font-medium
            w-60
            h-8
          "
        >
           <option v-for="(value, key) in AllCur" :key="key" :value="key">
            {{ value[0] }}
          </option>
          </select
        ><br />
        <input
          v-model="v2"
          type="text"
          name=""
          id=""
          class="
            border-2
            text-blue-700
            border-black
            text-[25px]
            font-serif font-medium
            w-60
            h-8
            p-2
          "
        />
      </div>
     </div>
     <!-- convert button onclick function will performe -->
    <button
      class="
        bg-red-600
        text-white text-[20px]
        p-2
        font-serif font-bold
        rounded-md
        mt-4
      "
      @click="onclickk()"
    >
      Convert
    </button>

    {{}}
  </div>
</template>
 