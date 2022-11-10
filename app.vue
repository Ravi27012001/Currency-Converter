<script setup lang="ts">

 
// let AllCur = ref<[string,number][]>([
//   ["KWD",0.00378],
//   ["BHD",0.00459],
//   ["OR",0.0047],
//   ["BPS",0.01064],
//   ["EE",0.01221],
//   ["USD",0.01225],
//   ["BRD",0.01716],
//   ["NZD",0.0206],
//   ["AF",0.02194],
//   ["INR",1]

// ]);
 
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

function onclickk(){
const calculation = v1.value * (AllCur.value[c2.value][1] / AllCur.value[c1.value][1]);
console.log(calculation);
v2.value = calculation;
}
function exchange(){
  let t1 = ref(c1.value)
  c1.value = c2.value;
  c2.value = t1.value;

  let t2 = ref(v1.value);
  v1.value = v2.value;
  v2.value = t2.value
}
//  watch([c2],()=>{
//   console.log(AllCur.value.find((e:[string,number])=>e[0]==c2.value))

//  },)


//  AllCur.value.find()
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
          <option v-for="(value, key) in AllCur" :key="key" :value="key">
            {{ value[0] }}
          </option>
          <!-- <option value="KWD">Kuwaiti Dinar</option>
          <option value="BHD">Bahaini Dinar</option>
          <option value="OR">Omani Rial</option>
          <option value="BPS">British Pound Sterling</option>
          <option value="EE">European Euro</option>
          <option value="USD">US Dollar</option>
          <option value="BRD">Brunei Dollar</option>
          <option value="NZD">New Zealand Dollar</option>
          <option value="AF">Aruban Florin</option>
          <option value="INR">Indian Rupee</option>
          -->
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
          <!-- <option value="KWD">Kuwaiti Dinar</option>
          <option value="BHD">Bahaini Dinar</option>
          <option value="OR">Omani Rial</option>
          <option value="BPS">British Pound Sterling</option>
          <option value="EE">European Euro</option>
          <option value="USD">US Dollar</option>
          <option value="BRD">Brunei Dollar</option>
          <option value="NZD">New Zealand Dollar</option>
          <option value="AF">Aruban Florin</option>
          <option value="INR">Indian Rupee</option> -->
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
 