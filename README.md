<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>VEHICLE GST PRICE</title>
  <style>
    body {
      margin: 0;
      font-family: Calibri, sans-serif;
      background: url("front-left-side-47.avif") no-repeat center center/cover;
      color: #fff;
      text-align: center;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
    }
    h1 {
      font-size: 2rem;
      margin: 15px 0;
      text-shadow: 2px 2px 6px rgba(0,0,0,0.6);
    }
    .inputs {
      margin: 10px 0;
      display: flex;
      gap: 10px;
      justify-content: center;
      flex-wrap: wrap;
    }
    .inputs input {
      padding: 8px;
      border-radius: 6px;
      border: none;
      outline: none;
      text-align: center;
      min-width: 180px;
      font-size: 1rem;
    }
    .calc-container {
      display: flex;
      justify-content: center;
      align-items: stretch;
      flex-wrap: wrap;
      gap: 15px;
      flex: 1;
      padding: 10px;
      box-sizing: border-box;
    }
    .calculator {
      flex: 1 1 300px;
      max-width: 340px;
      padding: 15px;
      border-radius: 16px;
      background: rgba(255, 255, 255, 0.12);
      backdrop-filter: blur(10px);
      color: #fff;
      text-align: center;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }
    #calc1 { border: 2px solid orange; }
    #calc2 { border: 2px solid #00aaff; }
    #calc3 { border: 2px solid yellow; }
    .title {
      font-size: 1.3rem;
      font-weight: bold;
      margin-bottom: 10px;
      padding: 6px;
      border-radius: 8px;
      background: rgba(255,255,255,0.15);
    }
    .title.orange { color: orange; border: 2px solid orange; }
    .title.blue { color: #00aaff; border: 2px solid #00aaff; }
    .title.yellow { color: yellow; border: 2px solid yellow; }
    .feature-box {
      background: rgba(255,255,255,0.15);
      padding: 8px;
      margin: 5px 0;
      border-radius: 10px;
      cursor: pointer;
      transition: all 0.2s ease;
      font-size: 0.95rem;
    }
    .feature-box:hover {
      background: rgba(255,255,255,0.25);
      transform: scale(1.03);
    }
    button {
      margin-top: 8px;
      padding: 8px;
      border: none;
      border-radius: 8px;
      font-weight: bold;
      cursor: pointer;
      background: rgba(255,255,255,0.2);
      color: white;
      transition: 0.2s;
    }
    button:hover {
      background: rgba(255,255,255,0.4);
    }
    .tooltip {
      position: fixed;
      bottom: 20px;
      left: 50%;
      transform: translateX(-50%);
      padding: 8px 16px;
      border-radius: 8px;
      backdrop-filter: blur(8px);
      font-weight: bold;
      animation: floatUp 1.2s ease forwards;
      z-index: 1000;
      font-size: 0.9rem;
    }
    @keyframes floatUp {
      0% {opacity:0; transform:translate(-50%,20px);}
      50% {opacity:1; transform:translate(-50%,-5px);}
      100% {opacity:0; transform:translate(-50%,-30px);}
    }
    .success {background:rgba(0,255,100,0.2);border:1px solid rgba(0,255,100,0.6);}
    .error {background:rgba(255,0,50,0.2);border:1px solid rgba(255,0,50,0.6);}
    footer {
      text-align: center;
      padding: 10px;
      font-size: 1rem;
      font-weight: bold;
      color: #fff;
      text-shadow: 1px 1px 4px rgba(0,0,0,0.6);
    }
  </style>
</head>
<body>
  <h1>VEHICLE GST PRICE</h1>

  <div class="inputs">
    <input type="number" id="exshowroom" placeholder="Ex-Showroom Price">
    <input type="number" id="discount" placeholder="Discount">
  </div>

  <div class="calc-container">
    <!-- Calc 1 -->
    <div class="calculator" id="calc1">
      <h2 class="title orange">GST 18%</h2>
      <div class="feature-box" onclick="copyValue('price1')">Price of Vehicle: <span id="price1">0</span></div>
      <div class="feature-box" onclick="copyValue('discount1')">Discount: <span id="discount1">0</span></div>
      <div class="feature-box" onclick="copyValue('assess1')">Assessable Value: <span id="assess1">0</span></div>
      <div class="feature-box" onclick="copyValue('cgst1')">CGST @ 9%: <span id="cgst1">0</span></div>
      <div class="feature-box" onclick="copyValue('sgst1')">SGST @ 9%: <span id="sgst1">0</span></div>
      <div class="feature-box" onclick="copyValue('invoice1')"><b>Invoice Price:</b> <span id="invoice1">0</span></div>
      <button onclick="convertToWords(1)">Convert to Word</button>
    </div>

    <!-- Calc 2 -->
    <div class="calculator" id="calc2">
      <h2 class="title blue">GST 40% + TCS 1%</h2>
      <div class="feature-box" onclick="copyValue('price2')">Price of Vehicle: <span id="price2">0</span></div>
      <div class="feature-box" onclick="copyValue('discount2')">Discount: <span id="discount2">0</span></div>
      <div class="feature-box" onclick="copyValue('assess2')">Assessable Value: <span id="assess2">0</span></div>
      <div class="feature-box" onclick="copyValue('cgst2')">CGST @ 20%: <span id="cgst2">0</span></div>
      <div class="feature-box" onclick="copyValue('sgst2')">SGST @ 20%: <span id="sgst2">0</span></div>
      <div class="feature-box" onclick="copyValue('tcs2')">TCS @ 1%: <span id="tcs2">0</span></div>
      <div class="feature-box" onclick="copyValue('invoice2')"><b>Invoice Price:</b> <span id="invoice2">0</span></div>
      <button onclick="convertToWords(2)">Convert to Word</button>
    </div>

    <!-- Calc 3 -->
    <div class="calculator" id="calc3">
      <h2 class="title yellow">GST 40% (No TCS)</h2>
      <div class="feature-box" onclick="copyValue('price3')">Price of Vehicle: <span id="price3">0</span></div>
      <div class="feature-box" onclick="copyValue('discount3')">Discount: <span id="discount3">0</span></div>
      <div class="feature-box" onclick="copyValue('assess3')">Assessable Value: <span id="assess3">0</span></div>
      <div class="feature-box" onclick="copyValue('cgst3')">CGST @ 20%: <span id="cgst3">0</span></div>
      <div class="feature-box" onclick="copyValue('sgst3')">SGST @ 20%: <span id="sgst3">0</span></div>
      <div class="feature-box" onclick="copyValue('invoice3')"><b>Invoice Price:</b> <span id="invoice3">0</span></div>
      <button onclick="convertToWords(3)">Convert to Word</button>
    </div>
  </div>

  <div style="margin:10px;">
    <button onclick="resetAll()">RESET ALL</button>
  </div>

  <footer>
    <p>Created by <b>Jithu</b></p>
  </footer>

  <script>
    const exInput=document.getElementById("exshowroom");
    const discInput=document.getElementById("discount");
    exInput.addEventListener("input",calculateAll);
    discInput.addEventListener("input",calculateAll);

    function calculateAll(){
      let ex=parseFloat(exInput.value)||0;
      let dis=parseFloat(discInput.value)||0;

      // Calc1
      let v1=ex/118*100, d1=dis/118*100, a1=v1-d1;
      let cg1=a1*0.09, sg1=a1*0.09, tot1=a1+cg1+sg1;
      updateCalc(1,v1,d1,a1,cg1,sg1,0,tot1);

      // Calc2
      let v2=ex/140*100, d2=dis/140*100, a2=v2-d2;
      let cg2=a2*0.20, sg2=a2*0.20, tcs2=(a2+cg2+sg2)*0.01;
      let tot2=a2+cg2+sg2+tcs2;
      updateCalc(2,v2,d2,a2,cg2,sg2,tcs2,tot2);

      // Calc3
      let v3=ex/140*100, d3=dis/140*100, a3=v3-d3;
      let cg3=a3*0.20, sg3=a3*0.20, tot3=a3+cg3+sg3;
      updateCalc(3,v3,d3,a3,cg3,sg3,0,tot3);
    }

    function updateCalc(num,v,d,a,cg,sg,tcs,tot){
      document.getElementById("price"+num).innerText=Math.round(v);
      document.getElementById("discount"+num).innerText=Math.round(d);
      document.getElementById("assess"+num).innerText=Math.round(a);
      document.getElementById("cgst"+num).innerText=Math.round(cg);
      document.getElementById("sgst"+num).innerText=Math.round(sg);
      if(document.getElementById("tcs"+num)) document.getElementById("tcs"+num).innerText=Math.round(tcs);
      document.getElementById("invoice"+num).innerText=Math.round(tot);
    }

    function copyValue(id){
      let val=document.getElementById(id).innerText;
      if(val && val!="0"){
        navigator.clipboard.writeText(val);
        showTooltip("Copied: "+val);
      }
    }

    function convertToWords(num){
      let val=document.getElementById(`invoice${num}`).innerText;
      if(val=="0"||val==""){showTooltip("Invoice Empty!",true);return;}
      let words=numberToWordsIndian(parseInt(val))+" Only";
      navigator.clipboard.writeText(words);
      showTooltip("Copied: "+words);
    }

    function resetAll(){
      exInput.value=""; discInput.value="";
      updateCalc(1,0,0,0,0,0,0,0);
      updateCalc(2,0,0,0,0,0,0,0);
      updateCalc(3,0,0,0,0,0,0,0);
      showTooltip("All Reset Done!");
    }

    function numberToWordsIndian(num){
      const ones=["","One","Two","Three","Four","Five","Six","Seven","Eight","Nine","Ten",
        "Eleven","Twelve","Thirteen","Fourteen","Fifteen","Sixteen","Seventeen","Eighteen","Nineteen"];
      const tens=["","","Twenty","Thirty","Forty","Fifty","Sixty","Seventy","Eighty","Ninety"];
      function toWords(n){
        if(n<20)return ones[n];
        if(n<100)return tens[Math.floor(n/10)]+" "+ones[n%10];
        if(n<1000)return ones[Math.floor(n/100)]+" Hundred "+toWords(n%100);
        if(n<100000)return toWords(Math.floor(n/1000))+" Thousand "+toWords(n%1000);
        if(n<10000000)return toWords(Math.floor(n/100000))+" Lakh "+toWords(n%100000);
        return toWords(Math.floor(n/10000000))+" Crore "+toWords(n%10000000);
      }
      return toWords(num).replace(/\s+/g," ").trim();
    }

    function showTooltip(msg,error=false){
      let tip=document.createElement("div");
      tip.className="tooltip "+(error?"error":"success");
      tip.innerText=msg;
      document.body.appendChild(tip);
      setTimeout(()=>{tip.remove();},1200);
    }
  </script>
</body>
</html>
