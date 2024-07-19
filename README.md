<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Skin Analysis Quiz</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #D8BFAA;
            color: #333;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }
        .container {
            width: 100%;
            max-width: 800px;
            margin: 20px;
            padding: 20px;
            background-color: #fff;
            border-radius: 12px;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
        }
        h1 {
            text-align: center;
            color: #8B4513;
            margin-bottom: 20px;
        }
        .question {
            margin-bottom: 20px;
        }
        .question label {
            display: block;
            margin-bottom: 10px;
            font-weight: bold;
            color: #8B4513;
        }
        .question input[type="radio"],
        .question input[type="checkbox"] {
            margin-right: 10px;
        }
        .submit-button {
            display: block;
            width: 100%;
            padding: 15px;
            background-color: #8B4513;
            color: #fff;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        .submit-button:hover {
            background-color: #A0522D;
        }
        .result {
            display: none;
            margin-top: 20px;
        }
        .result h2 {
            text-align: center;
            color: #8B4513;
        }
        .result p {
            font-size: 18px;
            color: #555;
        }
        .result .highlight {
            font-weight: bold;
            color: #8B4513;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Personalized Skin Analysis Quiz</h1>
        <form id="skinQuiz">
            <!-- Skin Type Identification Questions -->
            <div class="question">
                <label>How does your skin feel a few hours after cleansing?</label>
                <input type="radio" name="skinFeel" value="oily"> Oily and shiny<br>
                <input type="radio" name="skinFeel" value="dry"> Dry and tight<br>
                <input type="radio" name="skinFeel" value="normal"> Normal or balanced<br>
                <input type="radio" name="skinFeel" value="sensitive"> Sensitive or irritated
            </div>

            <div class="question">
                <label>How often do you experience breakouts?</label>
                <input type="radio" name="breakouts" value="frequent"> Frequently<br>
                <input type="radio" name="breakouts" value="occasional"> Occasionally<br>
                <input type="radio" name="breakouts" value="rare"> Rarely<br>
                <input type="radio" name="breakouts" value="never"> Never
            </div>

            <div class="question">
                <label>How visible are your pores?</label>
                <input type="radio" name="pores" value="large"> Large and visible<br>
                <input type="radio" name="pores" value="small"> Small and barely visible<br>
                <input type="radio" name="pores" value="normal"> Normal size<br>
                <input type="radio" name="pores" value="notSure"> Not sure
            </div>

            <div class="question">
                <label>How does your skin react to new products?</label>
                <input type="radio" name="react" value="easilyIrritated"> Easily irritated or red<br>
                <input type="radio" name="react" value="sometimesIrritated"> Sometimes irritated<br>
                <input type="radio" name="react" value="rarelyIrritated"> Rarely irritated<br>
                <input type="radio" name="react" value="neverIrritated"> Never irritated
            </div>

            <!-- Skin Concerns -->
            <div class="question">
                <label>What are your primary skin concerns? (Select all that apply)</label>
                <input type="checkbox" name="concerns" value="acne"> Acne<br>
                <input type="checkbox" name="concerns" value="darkCircles"> Dark circles<br>
                <input type="checkbox" name="concerns" value="darkSpots"> Dark spots<br>
                <input type="checkbox" name="concerns" value="unevenTone"> Uneven skin tone<br>
                <input type="checkbox" name="concerns" value="fineLines"> Fine lines<br>
                <input type="checkbox" name="concerns" value="wrinkles"> Wrinkles<br>
                <input type="checkbox" name="concerns" value="roughSkin"> Rough skin<br>
                <input type="checkbox" name="concerns" value="chappedLips"> Chapped lips<br>
                <input type="checkbox" name="concerns" value="tanning"> Tanning
            </div>

            <!-- Specific Concerns Questions -->
            <div class="question acne">
                <label>How severe is your acne?</label>
                <input type="radio" name="acneSeverity" value="mild"> Mild (occasional pimples)<br>
                <input type="radio" name="acneSeverity" value="moderate"> Moderate (regular breakouts)<br>
                <input type="radio" name="acneSeverity" value="severe"> Severe (cystic acne)
            </div>

            <div class="question darkCircles">
                <label>What do your dark circles look like?</label>
                <input type="radio" name="darkCirclesType" value="bluePurple"> Blue or purple<br>
                <input type="radio" name="darkCirclesType" value="brownBlack"> Brown or black<br>
                <input type="radio" name="darkCirclesType" value="puffy"> Puffy and swollen
            </div>

            <div class="question darkSpots">
                <label>How long have you had dark spots?</label>
                <input type="radio" name="darkSpotsDuration" value="recent"> Recently appeared<br>
                <input type="radio" name="darkSpotsDuration" value="months"> For several months<br>
                <input type="radio" name="darkSpotsDuration" value="years"> For years
            </div>

            <div class="question unevenTone">
                <label>Which areas of your face have an uneven skin tone?</label>
                <input type="radio" name="unevenToneAreas" value="forehead"> Forehead<br>
                <input type="radio" name="unevenToneAreas" value="cheeks"> Cheeks<br>
                <input type="radio" name="unevenToneAreas" value="mouth"> Around the mouth<br>
                <input type="radio" name="unevenToneAreas" value="overall"> Overall face
            </div>

            <div class="question fineLines">
                <label>Where do you notice fine lines and wrinkles?</label>
                <input type="radio" name="fineLinesLocation" value="forehead"> Forehead<br>
                <input type="radio" name="fineLinesLocation" value="eyes"> Around the eyes<br>
                <input type="radio" name="fineLinesLocation" value="mouth"> Around the mouth<br>
                <input type="radio" name="fineLinesLocation" value="overall"> Overall face
            </div>

            <div class="question roughSkin">
                <label>How often do you experience rough or textured skin?</label>
                <input type="radio" name="roughSkinFrequency" value="frequent"> Frequently<br>
                <input type="radio" name="roughSkinFrequency" value="occasional"> Occasionally<br>
                <input type="radio" name="roughSkinFrequency" value="rare"> Rarely
            </div>

            <div class="question chappedLips">
                <label>How often do your lips feel chapped or dry?</label>
                <input type="radio" name="chappedLipsFrequency" value="frequent"> Frequently<br>
                <input type="radio" name="chappedLipsFrequency" value="occasional"> Occasionally<br>
                <input type="radio" name="chappedLipsFrequency" value="rare"> Rarely
            </div>

            <div class="question tanning">
                <label>How often are you exposed to the sun without protection?</label>
                <input type="radio" name="tanningFrequency" value="frequent"> Frequently<br>
                <input type="radio" name="tanningFrequency" value="occasional"> Occasionally<br>
                <input type="radio" name="tanningFrequency" value="rare"> Rarely
            </div>

            <!-- Lifestyle and Habits -->
            <div class="question">
                <label>How much water do you drink daily?</label>
                <input type="radio" name="waterIntake" value="less1"> Less than 1 liter<br>
                <input type="radio" name="waterIntake" value="1to2"> 1-2 liters<br>
                <input type="radio" name="waterIntake" value="more2"> More than 2 liters
            </div>

            <div class="question">
                <label>How many hours of sleep do you get on average?</label>
                <input type="radio" name="sleep" value="less5"> Less than 5 hours<br>
                <input type="radio" name="sleep" value="5to7"> 5-7 hours<br>
                <input type="radio" name="sleep" value="more7"> More than 7 hours
            </div>

            <div class="question">
                <label>How often do you exercise?</label>
                <input type="radio" name="exercise" value="rarely"> Rarely<br>
                <input type="radio" name="exercise" value="1to2"> 1-2 times a week<br>
                <input type="radio" name="exercise" value="3to5"> 3-5 times a week<br>
                <input type="radio" name="exercise" value="daily"> Daily
            </div>

            <div class="question">
                <label>Do you follow a skincare routine?</label>
                <input type="radio" name="skincareRoutine" value="yes"> Yes, regularly<br>
                <input type="radio" name="skincareRoutine" value="sometimes"> Sometimes<br>
                <input type="radio" name="skincareRoutine" value="rarely"> Rarely<br>
                <input type="radio" name="skincareRoutine" value="never"> Never
            </div>

            <button type="button" class="submit-button" onclick="calculateResult()">Submit</button>
        </form>

        <div id="result" class="result">
            <h2>Your Skin Analysis Result</h2>
            <p id="skinType"></p>
            <p id="skinConcerns"></p>
            <p id="skinHealth"></p>
            <p class="highlight">To improve your skin health and to treat all your skin concerns, get help from our expert-designed skincare guide. Discover products on our website.</p>
        </div>
    </div>

    <script>
        function calculateResult() {
            const form = document.forms['skinQuiz'];
            const skinType = form['skinFeel'].value;
            const breakouts = form['breakouts'].value;
            const pores = form['pores'].value;
            const react = form['react'].value;

            const concerns = form['concerns'];
            let selectedConcerns = [];
            for (let concern of concerns) {
                if (concern.checked) {
                    selectedConcerns.push(concern.nextSibling.textContent.trim());
                }
            }

            const waterIntake = form['waterIntake'].value;
            const sleep = form['sleep'].value;
            const exercise = form['exercise'].value;
            const skincareRoutine = form['skincareRoutine'].value;

            let skinHealthScore = 0;

            // Skin Health Calculation
            if (waterIntake === 'more2') skinHealthScore += 10;
            else if (waterIntake === '1to2') skinHealthScore += 5;

            if (sleep === 'more7') skinHealthScore += 10;
            else if (sleep === '5to7') skinHealthScore += 5;

            if (exercise === 'daily') skinHealthScore += 10;
            else if (exercise === '3to5') skinHealthScore += 5;
            else if (exercise === '1to2') skinHealthScore += 3;

            if (skincareRoutine === 'yes') skinHealthScore += 10;
            else if (skincareRoutine === 'sometimes') skinHealthScore += 5;
            else if (skincareRoutine === 'rarely') skinHealthScore += 3;

            const skinHealthPercentage = skinHealthScore;

            let skinTypeResult = '';
            if (skinType === 'oily') {
                skinTypeResult = 'Oily Skin';
            } else if (skinType === 'dry') {
                skinTypeResult = 'Dry Skin';
            } else if (skinType === 'normal') {
                skinTypeResult = 'Normal Skin';
            } else if (skinType === 'sensitive') {
                skinTypeResult = 'Sensitive Skin';
            }

            document.getElementById('skinType').textContent = `Your skin type is: ${skinTypeResult}`;
            document.getElementById('skinConcerns').textContent = `Your primary skin concerns are: ${selectedConcerns.join(', ')}`;
            document.getElementById('skinHealth').textContent = `Your skin health score is: ${skinHealthPercentage}%`;

            document.getElementById('result').style.display = 'block';
        }
    </script>
</body>
</html>
