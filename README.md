<!DOCTYPE html>
<html>
<head>
  <title>BMR 計算器</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      padding: 20px;
    }
    
    h1 {
      margin-bottom: 20px;
    }
    
    label {
      display: block;
      margin-bottom: 10px;
    }
    
    input {
      padding: 5px;
    }
  </style>
</head>
<body>
  <h1>BMR 計算器</h1>
  
  <form>
    <label for="gender">性別:</label>
    <input type="radio" name="gender" value="male" checked> 男性
    <input type="radio" name="gender" value="female"> 女性
    
    <br><br>
    
    <label for="age">年齡:</label>
    <input type="number" name="age" id="age" required>
    
    <br><br>
    
    <label for="weight">體重 (公斤):</label>
    <input type="number" name="weight" id="weight" required>
    
    <br><br>
    
    <label for="height">身高 (公分):</label>
    <input type="number" name="height" id="height" required>
    
    <br><br>
    
    <label for="activity">活動量:</label>
    <select name="activity" id="activity" required>
      <option value="sedentary">久坐 (辦公室工作，很少運動)</option>
      <option value="lightlyActive">輕度活動 (輕度運動或運動2-3天/週)</option>
      <option value="moderatelyActive">中度活動 (中度運動或運動4-5天/週)</option>
      <option value="veryActive">高度活動 (高度運動或運動6-7天/週)</option>
      <option value="extraActive">極度活動 (非常劇烈運動或體力勞動工作)</option>
    </select>

    
    
    <br><br>
    
    <input type="submit" value="計算">
  </form>
  
  <br>
  
  <div id="result"></div>
  
  <script>
    document.querySelector("form").addEventListener("submit", function(event) {
      event.preventDefault();
      
      var gender = document.querySelector("input[name='gender']:checked").value;
      var age = document.getElementById("age").value;
      var weight = document.getElementById("weight").value;
      var height = document.getElementById("height").value;
      var activity = document.getElementById("activity").value;
      
      // 計算BMR
      var bmr = 0;
      if (gender === "male") {
        bmr = 66 + (13.75 * weight) + (5 * height) - (6.75 * age);
      } else {
        bmr = 655 + (9.56 * weight) + (1.85 * height) - (4.68 * age);
      }
        var tdee = 0;
      if (activity === "sedentary") {
        tdee = bmr * 1.2;
      } else if (activity === "lightlyActive") {
        tdee = bmr * 1.375;
      } else if (activity === "moderatelyActive") {
        tdee = bmr * 1.55;
      } else if (activity === "veryActive") {
        tdee = bmr * 1.725;
      } else if (activity === "extraActive") {
        tdee = bmr * 1.9;
      }
      
      document.getElementById("result").innerHTML = "您的基礎代謝率 (BMR) 是: " + bmr.toFixed(2) + " 大卡<br>";
      document.getElementById("result").innerHTML += "您的總消耗熱量 (TDEE) 是: " + tdee.toFixed(2) + " 大卡";
    });
  </script>
</body>
</html>
      

