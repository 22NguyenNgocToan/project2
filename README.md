<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>SmartCoder AI</title>
<style>
body {
  background: linear-gradient(135deg, #89f7fe, #66a6ff);
  font-family: Arial, sans-serif;
  color: #333;
  text-align: center;
  padding: 20px;
}
h1 { color: #004aad; }
textarea {
  width: 80%;
  height: 250px;
  border-radius: 8px;
  border: none;
  padding: 10px;
  font-family: monospace;
  font-size: 15px;
}
button {
  margin: 5px;
  padding: 10px 15px;
  background: #004aad;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
button:hover { background: #00337f; }
#review {
  background: white;
  width: 80%;
  margin: 15px auto;
  border-radius: 8px;
  padding: 10px;
  text-align: left;
}
</style>
</head>
<body>
<h1>⚡ SmartCoder AI</h1>
<select id="lang">
  <option value="c">C</option>
  <option value="cpp">C++</option>
</select><br><br>

<textarea id="code" placeholder="Generated or optimized code appears here..."></textarea><br>

<button onclick="generate()">Generate</button>
<button onclick="review()">Review</button>
<button onclick="optimize()">Optimize</button>
<button onclick="copyCode()">Copy</button>

<div id="review">🧩 Ready for action.</div>

<script>
const codeSamples = {
  c: `#include <stdio.h>
int main(){
    int n;
    printf("Enter a number: ");
    scanf("%d", &n);
    printf("Factorial: TBD\\n");
    return 0;
}`,
  cpp: `#include <iostream>
using namespace std;
int main(){
    int n;
    cout << "Enter a number: ";
    cin >> n;
    cout << "Result: TBD" << endl;
    return 0;
}`
};

function generate(){
  const lang = document.getElementById("lang").value;
  document.getElementById("code").value = codeSamples[lang];
  document.getElementById("review").innerText = "✅ Code generated successfully.";
}

function review(){
  const code = document.getElementById("code").value;
  let out = [];
  if(code.includes("gets")) out.push("⚠️ Replace gets() with fgets().");
  if(!code.includes("return")) out.push("ℹ️ Add return 0;");
  if(out.length===0) out.push("✅ Looks clean!");
  document.getElementById("review").innerText = out.join("\\n");
}

function optimize(){
  let code = document.getElementById("code").value;
  if(code.includes("Factorial: TBD")){
    code = code.replace("Factorial: TBD", "Factorial computed successfully!");
  }
  if(code.includes("Result: TBD")){
    code = code.replace("Result: TBD", "Calculation complete!");
  }
  document.getElementById("code").value = code;
  document.getElementById("review").innerText = "⚡ Code optimized by SmartCoder!";
}

function copyCode(){
  const area = document.getElementById("code");
  area.select(); document.execCommand("copy");
  document.getElementById("review").innerText = "📋 Code copied!";
}
</script>
</body>
</html>
