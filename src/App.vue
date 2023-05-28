<template>
  <div
    class="navbar w-full h-[60px] flex justify-center items-center bg-orange-500"
  >
    <h1 class="text-white text-2xl">รางวัลล็อตเตอรี่ Diversition</h1>
  </div>
  <main class="min-h-screen bg-[#0d1a2d]">
    <div class="w-full h-full">
      <div class="flex justify-center items-center w-full min-h-full">
        <div
          class="w-full md:w-[70%] min-h-[500px] bg-slate-40 mt-2 md:mt-[55px]  rounded-md border border-slate-600 shadow-2xl"
        >
          <div
            class="w-full h-[60px] bg-blue-600 flex justify-center items-center rounded-md p-5"
          >
            <p class="text-lg text-white">
              ผลการออกรางวัลล็อตเตอรี่ Diversition
            </p>
          </div>
          <div class="w-full flex justify-center items-center mx-auto my-3 p-1">
            <button
              @click="getRandomNumber()"
              class="bg-orange-500 w-[90px] h-[40px] rounded-lg text-white hover:bg-orange-400 hover:text-black transition"
            >
              สุ่มรางวัล
            </button>
          </div>
          <div class="blcok mt-2 w-full p-1">
            <div class="columns-1 md:columns-4 gap-x-0">
              <div class="bg-slate-300 border border-slate-600 h-[150px]">
                <div
                  class="h-[40%] bg-slate-500 flex flex-col items-center justify-center"
                >
                  <p class="text-center font-bold text-white">รางวัลที่ 1</p>
                  <p class="text-center font-bold text-white text-[11.5px]">
                    มีจำนวน 1 รางวัล
                  </p>
                </div>
                <div class="h-[60%] flex flex-col justify-center items-center">
                  <h3 class="text-[35px]">
                    {{ !this.threeDigitLotteryNumbers[0]? "XXX" : this.threeDigitLotteryNumbers[0]  }}
                  </h3>
                </div>
              </div>

              <div class="bg-slate-300 border border-slate-600 h-[150px]">
                <div
                  class="h-[40%] bg-slate-500 flex flex-col items-center justify-center"
                >
                  <p class="text-center font-bold text-white">รางวัลที่ 2</p>
                  <p class="text-center  text-white font-bold text-[11.5px]">
                    มีจำนวน 3 รางวัล
                  </p>
                </div>
                <div class="w-full h-[60%] flex items-center justify-evenly">
                  <h3 class="text-[24px]">
                    {{ !this.threeDigitLotteryNumbers[1] ? "XXX" : this.threeDigitLotteryNumbers[1]  }}
                  </h3>
                  <h3 class="text-[24px]">
                    {{ !this.threeDigitLotteryNumbers[2] ? "XXX" : this.threeDigitLotteryNumbers[2] }}
                  </h3>
                  <h3 class="text-[24px]">
                    {{ !this.threeDigitLotteryNumbers[3] ? "XXX" : this.threeDigitLotteryNumbers[3] }}
                  </h3>
                </div>
              </div>
              <div class="bg-slate-300 border border-slate-600 h-[150px]">
                <div
                  class="h-[40%] bg-slate-500 flex flex-col items-center justify-center"
                >
                  <p class="text-center font-bold text-white lg:text-lg">
                    รางวัลข้างเคียงรางวัลที่ 1
                  </p>
                  <p class="text-center text-white font-bold text-[11.5px]">
                    มีจำนวน 1 รางวัล
                  </p>
                </div>
                <div class="w-full h-[60%] flex justify-evenly items-center">
                  <h3 class="text-[24px]">
                    {{ !this.threeDigitLotteryNumbers[0] + 1 == 2 ? "XXX" : this.threeDigitLotteryNumbers[0] + 1   }}
                  </h3>
                  <h3 class="text-[24px]">
                    {{ !this.threeDigitLotteryNumbers[0] - 1 == 0 ? "XXX" : this.threeDigitLotteryNumbers[0] - 1   }}
                  </h3>
                </div>
              </div>
              <div class="bg-slate-300 border border-slate-600 h-[150px]">
                <div
                  class="h-[40%] bg-slate-500 flex flex-col items-center justify-center"
                >
                  <p class="text-center text-white font-bold">รางวัลเลขท้าย 2 ตัว</p>
                  <p class="text-center font-bold text-white text-[11.5px]">
                    มีจำนวน 1 รางวัล
                  </p>
                </div>
                <div class="h-[60%] flex-col flex justify-center items-center">
                  <h3 class="text-[35px]">{{ !twoDigitLotteryNumbers[0] ? "XX" : twoDigitLotteryNumbers[0] }}</h3>
                </div>
              </div>
            </div>
            <div class="w-full flex justify-center mt-3">
              <div
                class="w-full flex flex-col justify-center bg-slate-300 p-2 rounded-md border border-slate-600"
              >
                <p class="text-center text-xl">ตรวจรางวัล Diversition</p>
                <div class="flex justify-center p-4">
                  <div class="w-full flex flex-col justify-center items-center">
                    <input
                      type="text"
                      pattern="[0-9]*"
                      inputmode="numeric"
                      maxlength="3"
                      v-model="inputchecklotto"
                      class="border-slate-200 placeholder-slate-400 contrast-more:border-slate-400 contrast-more:placeholder-slate-500 px-2 py-1"
                      placeholder="โปรดกรอกหมายเลขรางวัล"
                    
                    />
                    <button
                      @click.prevent="checkWinnerPrizes"
                      class="mt-4 bg-blue-300 w-[120px] h-[40px] rounded-lg p-1 hover:bg-blue-600 transition-all"
                    >
                      ตรวจสอบรางวัล
                    </button>
                    <Transition name="fade">
                    <div v-show="this.yourPrize[0]" class="mt-5 mb-5 w-[1-0%] md:w-[50%] h-[70px] bg-slate-600 flex justify-center items-center rounded-md">
                      <p class="text-white text-center p-3"> ผลรางวัลของคุณคือ : {{ this.yourPrize[0] }} </p>
                    </div>
                  </Transition>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  data() {
    return {
      threeDigitLotteryNumbers: [],
      twoDigitLotteryNumbers: [],
      inputchecklotto: [],
      yourPrize: [],
    };
  },
  mounted(){
     this.ReadCookie();
  },
  methods: {
  getRandomNumber() {
    this.threeDigitLotteryNumbers = [];
    this.twoDigitLotteryNumbers = [];
    for (let i = 0; i < 4; i++) {
      const threeDigitNumber = Math.floor(Math.random() * 900) + 100;
      this.threeDigitLotteryNumbers.push(threeDigitNumber);
    }
    const twoDigitNumber = Math.floor(Math.random() * 90) + 10;
    this.twoDigitLotteryNumbers.push(twoDigitNumber);

    const SaverandomNumbers = {
      threeDigitLotteryNumbers: this.threeDigitLotteryNumbers,
      twoDigitLotteryNumbers: this.twoDigitLotteryNumbers
    };
    this.setCookie("randomNumbers", JSON.stringify(SaverandomNumbers));
  },

  ReadCookie(){
    const LottoNumnerByCookie = this.getCookie("randomNumbers")
    if(LottoNumnerByCookie){
      const FromCookieNumber  = JSON.parse(LottoNumnerByCookie)
      this.threeDigitLotteryNumbers = FromCookieNumber.threeDigitLotteryNumbers;
      this.twoDigitLotteryNumbers = FromCookieNumber.twoDigitLotteryNumbers
    }
    return;
  },

  getCookie(name){
  const value = "; " + document.cookie;
  const parts = value.split("; " + name + "=");
  if (parts.length === 2) {
    return parts.pop().split(";").shift();
  }
  return null;
},

  setCookie(name, value){
  const d = new Date();
  d.setTime(d.getTime() + (365 * 24 * 60 * 60 * 1000)); 
  const expires = "expires=" + d.toUTCString();
  //เพิ่มข้อมูลลงใน Cookie
  document.cookie = name + "=" + value + ";" + expires + ";path=/";
  },

  checkWinnerPrizes() {
    //Set Prize
    const inputNumber = String(this.inputchecklotto);
    const prizeNumbers = this.threeDigitLotteryNumbers;
    const twodigitSuffixPrize = this.twoDigitLotteryNumbers[0];
    const sidePrizeUp = String(this.threeDigitLotteryNumbers[0]+1);
    const sidePrizeDown = String(this.threeDigitLotteryNumbers[0]-1);
    
   //Set Prize
    const isMatchingFirstPrize = inputNumber === String(prizeNumbers[0]);
    const isMatchingSecondPrize = prizeNumbers.slice(1, 4).includes(Number(inputNumber));
    const isMatchingSuffixPrize = inputNumber.endsWith(String(twodigitSuffixPrize));
    const isMatchingSidePrizeUp = inputNumber === sidePrizeUp;
    const isMatchingSidePrizeDown = inputNumber === sidePrizeDown;
   
    const results = [];

    if (isMatchingFirstPrize 
      && isMatchingSuffixPrize) {
      results.push(`${inputNumber} ถูกรางวัลที่ 1 และรางวัลเลขท้าย 2 ตัว`);
    } else if (isMatchingFirstPrize) {
      results.push(`${inputNumber} ถูกรางวัลที่ 1`);
    }

    if (isMatchingSecondPrize 
      && isMatchingSuffixPrize) {
      results.push(`${inputNumber} ถูกรางวัลที่ 2 และรางวัลเลขท้าย 2 ตัว`);
    } else if (isMatchingSecondPrize) {
      results.push(`${inputNumber} ถูกรางวัลที่ 2`);
    }

    if(isMatchingSidePrizeUp  
      && isMatchingSuffixPrize){
      results.push(`${inputNumber} คุณถูกรางวัลข้างเคียงของรางวัลที่หนึ่ง และรางวัลเลขท้ายสองตัว`);
    } else if(isMatchingSidePrizeUp){
      results.push(`${inputNumber} คุณถูกรางวัลข้างเคียง`);
    }

    if(isMatchingSidePrizeDown 
      && isMatchingSuffixPrize){

      results.push(`${inputNumber} คุณถูกรางวัลข้างเคียงของรางวัลที่หนึ่ง และรางวัลเลขท้ายสองตัว`);

    }else if(isMatchingSidePrizeDown){

      results.push(`${inputNumber} คุณถูกรางวัลข้างเคียง`);

    }

    if (isMatchingSuffixPrize 
    && !isMatchingFirstPrize 
    && !isMatchingSecondPrize) {

      results.push(`${inputNumber} ถูกรางวัลเลขท้าย 2 ตัว`);

    }
    if(this.inputchecklotto == 0 && this.inputchecklotto < 2){
      results.push(`โปรดกรอกรางวัล หรือ กรุณาตรวจสอบความถูกต้อง`);
    }else if (!isMatchingFirstPrize 
      && !isMatchingSecondPrize 
      && !isMatchingSuffixPrize 
      && !isMatchingSidePrizeUp 
      && !isMatchingSidePrizeDown) {

      results.push(`${inputNumber} เสียใจด้วย คุณไม่ถูกรางวัล`);

    }

    this.yourPrize = results.slice(-2);
  }
  },
};
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.9s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
