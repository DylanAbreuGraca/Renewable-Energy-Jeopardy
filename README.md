<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Renewable Energy Jeopardy</title>
<style>
body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background: linear-gradient(to right, #00c6ff, #00ff85);
    color: #fff;
    text-align: center;
    margin: 0;
    padding: 0;
}

h1 {
    margin-top: 30px;
    font-size: 48px;
    text-shadow: 3px 3px #000;
}

table {
    margin: 30px auto;
    border-collapse: collapse;
    box-shadow: 0 6px 15px rgba(0,0,0,0.6);
}

th {
    padding: 25px;
    border: 2px solid #000;
    width: 200px;
    font-size: 24px;
    text-shadow: 1.5px 1.5px #000;
    color: #fff;
}

td {
    border: 2px solid #000;
    padding: 35px;
    font-size: 28px;
    cursor: pointer;
    transition: background 0.3s, transform 0.2s;
    border-radius: 12px;
    color: #fff;
}

td:hover {
    transform: scale(1.1);
}

td.used {
    background: #003366 !important;
    color: #bbb !important;
    cursor: default;
}

#questionBox {
    margin-top: 40px;
    padding: 35px;
    background: rgba(0,0,0,0.75);
    border-radius: 20px;
    width: 75%;
    margin-left: auto;
    margin-right: auto;
    display: none;
    font-size: 30px;
    text-align: center;
    box-shadow: 0 6px 15px rgba(0,0,0,0.6);
    color: #fff;
}

#showAnswerBtn {
    margin-top: 25px;
    padding: 15px 30px;
    font-size: 24px;
    border: none;
    border-radius: 12px;
    background: #ff9900;
    color: #000;
    cursor: pointer;
    transition: background 0.3s;
}

#showAnswerBtn:hover {
    background: #ffcc33;
}
</style>
</head>
<body>
<h1>Renewable Energy Jeopardy</h1>

<table>
  <tr>
    <th style="background:#FF5733">Types of Energy</th>
    <th style="background:#33FF57">How We Use It</th>
    <th style="background:#FFC300">Good for the Earth</th>
    <th style="background:#DAF7A6">Energy Around the World</th>
    <th style="background:#C700FF">Energy Words</th>
  </tr>
  <tr>
    <td onclick="showQ(0,0,this)" style="background:#FF8D33">100</td>
    <td onclick="showQ(1,0,this)" style="background:#33FF99">100</td>
    <td onclick="showQ(2,0,this)" style="background:#FFD633">100</td>
    <td onclick="showQ(3,0,this)" style="background:#B9FFB9">100</td>
    <td onclick="showQ(4,0,this)" style="background:#D16EFF">100</td>
  </tr>
  <tr>
    <td onclick="showQ(0,1,this)" style="background:#FF9933">200</td>
    <td onclick="showQ(1,1,this)" style="background:#33FFAA">200</td>
    <td onclick="showQ(2,1,this)" style="background:#FFDD33">200</td>
    <td onclick="showQ(3,1,this)" style="background:#CCFFCC">200</td>
    <td onclick="showQ(4,1,this)" style="background:#D966FF">200</td>
  </tr>
  <tr>
    <td onclick="showQ(0,2,this)" style="background:#FFB833">300</td>
    <td onclick="showQ(1,2,this)" style="background:#33FFBB">300</td>
    <td onclick="showQ(2,2,this)" style="background:#FFE033">300</td>
    <td onclick="showQ(3,2,this)" style="background:#E6FFE6">300</td>
    <td onclick="showQ(4,2,this)" style="background:#E066FF">300</td>
  </tr>
  <tr>
    <td onclick="showQ(0,3,this)" style="background:#FFCC33">400</td>
    <td onclick="showQ(1,3,this)" style="background:#33FFCC">400</td>
    <td onclick="showQ(2,3,this)" style="background:#FFF033">400</td>
    <td onclick="showQ(3,3,this)" style="background:#F0FFF0">400</td>
    <td onclick="showQ(4,3,this)" style="background:#FF99FF">400</td>
  </tr>
  <tr>
    <td onclick="showQ(0,4,this)" style="background:#FFD633">500</td>
    <td onclick="showQ(1,4,this)" style="background:#33FFDD">500</td>
    <td onclick="showQ(2,4,this)" style="background:#FFFF33">500</td>
    <td onclick="showQ(3,4,this)" style="background:#F5FFF5">500</td>
    <td onclick="showQ(4,4,this)" style="background:#FF66FF">500</td>
  </tr>
</table>

<div id="questionBox">
  <div id="questionText"></div>
  <button id="showAnswerBtn" onclick="showAnswer()">Show Answer</button>
</div>

<script>
const questions = [
  ["This energy comes from the sun.", "This energy uses moving air to make power.", "This energy comes from flowing water.", "This energy comes from heat inside the Earth.", "This energy uses plants or food waste."],
  ["Solar panels give us this type of power for homes.", "Wind energy can turn these big machines with blades.", "Hydroelectric dams help make this for cities.", "Solar energy can charge these devices we carry.", "Geothermal energy can heat this part of a building."],
  ["Renewable energy keeps this clean for us to breathe.", "Clean energy means we make less of this P-word.", "Water energy protects animals in this ecosystem.", "Solar and wind energy do NOT make this gas.", "Renewable energy protects animals like birds and fish."],
  ["This country is famous for windmills.", "This hot country uses many solar panels.", "Canada uses a lot of this energy because of rivers.", "Iceland uses lots of this Earth-heat energy.", "This continent has many deserts for solar power."],
  ["These flat objects on roofs collect sunlight.", "This word means energy used again and again.", "This word means the power that turns on lights.", "This machine spins when the wind blows.", "10-letter word that means making less waste."]
];

const answers = [
  ["Solar energy", "Wind energy", "Hydroelectric energy", "Geothermal energy", "Biomass energy"],
  ["Electricity", "Turbines", "Electricity", "Phones/Tablets", "Buildings/Houses"],
  ["Air", "Pollution", "River ecosystem", "Greenhouse gas", "Nature"],
  ["Denmark", "Spain/Saudi Arabia/South Africa", "Hydroelectric energy", "Geothermal energy", "Africa"],
  ["Solar panels", "Renewable", "Electricity", "Wind turbine", "Recycling"]
];

let current = {cat: null, row: null};

function showQ(cat, row, cell) {
  if (cell.classList.contains("used")) return;
  cell.classList.add("used");
  current.cat = cat;
  current.row = row;
  document.getElementById("questionText").innerText = questions[cat][row];
  document.getElementById("questionBox").style.display = "block";
}

function showAnswer() {
  if(current.cat !== null && current.row !== null){
    document.getElementById("questionText").innerText = answers[current.cat][current.row];
  }
}
</script>

</body>
</html>
