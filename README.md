<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Premium Skin Analysis Quiz | Master The Art of Skincare</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;500;600;700&family=Montserrat:wght@300;400;500;600&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #8B6B4A;
            --secondary: #D4BFA8;
            --accent: #C19A6B;
            --light: #F8F4EF;
            --dark: #3A2E1E;
            --success: #A8C69F;
            --warning: #E8C07D;
        }
        
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }
        
        body {
            font-family: 'Montserrat', sans-serif;
            background-color: var(--light);
            color: var(--dark);
            line-height: 1.6;
            background-image: url('https://images.unsplash.com/photo-1522335789203-aabd1fc54bc9?ixlib=rb-1.2.1&auto=format&fit=crop&w=1487&q=80');
            background-size: cover;
            background-attachment: fixed;
            background-position: center;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
        }
        
        .container {
            width: 100%;
            max-width: 900px;
            background-color: rgba(255, 255, 255, 0.95);
            border-radius: 16px;
            box-shadow: 0 10px 30px rgba(58, 46, 30, 0.2);
            overflow: hidden;
            position: relative;
            transition: all 0.3s ease;
        }
        
        .container:hover {
            box-shadow: 0 15px 40px rgba(58, 46, 30, 0.3);
        }
        
        .header {
            background: linear-gradient(135deg, var(--primary), var(--accent));
            color: white;
            padding: 30px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        
        .header::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('https://images.unsplash.com/photo-1522337360788-8b13dee7a37e?ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80') center/cover;
            opacity: 0.2;
            z-index: 0;
        }
        
        .header-content {
            position: relative;
            z-index: 1;
        }
        
        h1 {
            font-family: 'Playfair Display', serif;
            font-size: 2.5rem;
            margin-bottom: 10px;
            font-weight: 700;
            letter-spacing: 0.5px;
        }
        
        .subtitle {
            font-size: 1.1rem;
            opacity: 0.9;
            margin-bottom: 20px;
        }
        
        .progress-container {
            width: 100%;
            background-color: rgba(255, 255, 255, 0.3);
            border-radius: 10px;
            margin: 20px 0;
            height: 10px;
            overflow: hidden;
        }
        
        .progress-bar {
            height: 100%;
            background: linear-gradient(90deg, var(--light), var(--secondary));
            width: 0%;
            transition: width 0.5s ease;
            border-radius: 10px;
        }
        
        .quiz-content {
            padding: 30px;
        }
        
        .question-container {
            display: none;
            animation: fadeIn 0.5s ease;
        }
        
        .question-container.active {
            display: block;
        }
        
        .question {
            margin-bottom: 25px;
        }
        
        .question-number {
            font-family: 'Playfair Display', serif;
            color: var(--primary);
            font-size: 1.1rem;
            margin-bottom: 5px;
            font-weight: 600;
        }
        
        .question-text {
            font-size: 1.2rem;
            margin-bottom: 15px;
            font-weight: 500;
            color: var(--dark);
        }
        
        .options {
            display: grid;
            grid-template-columns: 1fr;
            gap: 12px;
        }
        
        .option {
            background-color: white;
            border: 1px solid #e0d6c9;
            border-radius: 8px;
            padding: 15px;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            position: relative;
            overflow: hidden;
        }
        
        .option:hover {
            border-color: var(--accent);
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(193, 154, 107, 0.1);
        }
        
        .option.selected {
            background-color: rgba(193, 154, 107, 0.1);
            border-color: var(--accent);
        }
        
        .option input {
            margin-right: 15px;
            cursor: pointer;
        }
        
        .option-label {
            flex-grow: 1;
        }
        
        .navigation {
            display: flex;
            justify-content: space-between;
            margin-top: 30px;
        }
        
        .btn {
            padding: 12px 25px;
            border-radius: 8px;
            border: none;
            font-family: 'Montserrat', sans-serif;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 1rem;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .btn-primary {
            background-color: var(--primary);
            color: white;
        }
        
        .btn-primary:hover {
            background-color: var(--accent);
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(139, 107, 74, 0.3);
        }
        
        .btn-secondary {
            background-color: transparent;
            color: var(--primary);
            border: 1px solid var(--primary);
        }
        
        .btn-secondary:hover {
            background-color: rgba(139, 107, 74, 0.1);
        }
        
        .btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
            transform: none !important;
            box-shadow: none !important;
        }
        
        .result-container {
            display: none;
            padding: 30px;
            animation: fadeIn 0.8s ease;
        }
        
        .result-header {
            text-align: center;
            margin-bottom: 30px;
        }
        
        .result-title {
            font-family: 'Playfair Display', serif;
            color: var(--primary);
            font-size: 2rem;
            margin-bottom: 10px;
        }
        
        .result-subtitle {
            color: var(--dark);
            opacity: 0.8;
            margin-bottom: 20px;
        }
        
        .result-card {
            background-color: white;
            border-radius: 12px;
            padding: 25px;
            margin-bottom: 20px;
            box-shadow: 0 5px 15px rgba(58, 46, 30, 0.05);
            border-left: 4px solid var(--accent);
        }
        
        .result-card-title {
            font-family: 'Playfair Display', serif;
            color: var(--primary);
            margin-bottom: 15px;
            font-size: 1.3rem;
        }
        
        .result-content {
            line-height: 1.8;
        }
        
        .highlight {
            color: var(--primary);
            font-weight: 600;
        }
        
        .ebook-promo {
            background: linear-gradient(135deg, var(--primary), var(--accent));
            color: white;
            padding: 30px;
            border-radius: 12px;
            margin-top: 40px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        
        .ebook-promo::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('https://images.unsplash.com/photo-1544947950-fa07a98d237f?ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80') center/cover;
            opacity: 0.1;
            z-index: 0;
        }
        
        .ebook-promo-content {
            position: relative;
            z-index: 1;
        }
        
        .ebook-title {
            font-family: 'Playfair Display', serif;
            font-size: 1.8rem;
            margin-bottom: 15px;
        }
        
        .ebook-description {
            margin-bottom: 20px;
            font-size: 1.1rem;
            opacity: 0.9;
            max-width: 700px;
            margin-left: auto;
            margin-right: auto;
        }
        
        .btn-ebook {
            background-color: white;
            color: var(--primary);
            font-weight: 600;
            padding: 15px 30px;
            border-radius: 50px;
            text-transform: uppercase;
            letter-spacing: 1px;
            font-size: 0.9rem;
            transition: all 0.3s ease;
            display: inline-block;
            text-decoration: none;
        }
        
        .btn-ebook:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(255, 255, 255, 0.2);
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .option-icon {
            margin-right: 15px;
            color: var(--accent);
            font-size: 1.2rem;
        }
        
        /* Responsive adjustments */
        @media (max-width: 768px) {
            .container {
                margin: 10px;
                padding: 0;
            }
            
            .header, .quiz-content, .result-container {
                padding: 20px;
            }
            
            h1 {
                font-size: 2rem;
            }
            
            .question-text {
                font-size: 1.1rem;
            }
            
            .btn {
                padding: 10px 20px;
            }
        }
        
        /* Custom radio and checkbox */
        input[type="radio"],
        input[type="checkbox"] {
            -webkit-appearance: none;
            -moz-appearance: none;
            appearance: none;
            width: 20px;
            height: 20px;
            border: 2px solid #d4b59e;
            border-radius: 50%;
            outline: none;
            transition: all 0.3s ease;
            position: relative;
            cursor: pointer;
        }
        
        input[type="checkbox"] {
            border-radius: 4px;
        }
        
        input[type="radio"]:checked,
        input[type="checkbox"]:checked {
            background-color: var(--accent);
            border-color: var(--accent);
        }
        
        input[type="radio"]:checked::after,
        input[type="checkbox"]:checked::after {
            content: "";
            position: absolute;
            width: 10px;
            height: 10px;
            background-color: white;
            border-radius: 50%;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }
        
        input[type="checkbox"]:checked::after {
            content: "✓";
            color: white;
            font-size: 12px;
            line-height: 1;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 0;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <div class="header-content">
                <h1>Premium Skin Analysis</h1>
                <p class="subtitle">Discover your unique skin profile and receive personalized recommendations</p>
                <div class="progress-container">
                    <div class="progress-bar" id="progressBar"></div>
                </div>
            </div>
        </div>
        
        <div class="quiz-content">
            <form id="skinQuiz">
                <!-- Question 1 -->
                <div class="question-container active" id="question1">
                    <div class="question">
                        <div class="question-number">Question 1 of 15</div>
                        <div class="question-text">How does your skin feel a few hours after cleansing?</div>
                        <div class="options">
                            <label class="option">
                                <input type="radio" name="skinFeel" value="oily">
                                <span class="option-label">Oily and shiny</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="skinFeel" value="dry">
                                <span class="option-label">Dry and tight</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="skinFeel" value="normal">
                                <span class="option-label">Normal or balanced</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="skinFeel" value="sensitive">
                                <span class="option-label">Sensitive or irritated</span>
                            </label>
                        </div>
                    </div>
                    <div class="navigation">
                        <button type="button" class="btn btn-secondary" disabled>Previous</button>
                        <button type="button" class="btn btn-primary next-btn">Next</button>
                    </div>
                </div>
                
                <!-- Question 2 -->
                <div class="question-container" id="question2">
                    <div class="question">
                        <div class="question-number">Question 2 of 15</div>
                        <div class="question-text">How often do you experience breakouts?</div>
                        <div class="options">
                            <label class="option">
                                <input type="radio" name="breakouts" value="frequent">
                                <span class="option-label">Frequently</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="breakouts" value="occasional">
                                <span class="option-label">Occasionally</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="breakouts" value="rare">
                                <span class="option-label">Rarely</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="breakouts" value="never">
                                <span class="option-label">Never</span>
                            </label>
                        </div>
                    </div>
                    <div class="navigation">
                        <button type="button" class="btn btn-secondary prev-btn">Previous</button>
                        <button type="button" class="btn btn-primary next-btn">Next</button>
                    </div>
                </div>
                
                <!-- Question 3 -->
                <div class="question-container" id="question3">
                    <div class="question">
                        <div class="question-number">Question 3 of 15</div>
                        <div class="question-text">How visible are your pores?</div>
                        <div class="options">
                            <label class="option">
                                <input type="radio" name="pores" value="large">
                                <span class="option-label">Large and visible</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="pores" value="small">
                                <span class="option-label">Small and barely visible</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="pores" value="normal">
                                <span class="option-label">Normal size</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="pores" value="notSure">
                                <span class="option-label">Not sure</span>
                            </label>
                        </div>
                    </div>
                    <div class="navigation">
                        <button type="button" class="btn btn-secondary prev-btn">Previous</button>
                        <button type="button" class="btn btn-primary next-btn">Next</button>
                    </div>
                </div>
                
                <!-- Question 4 -->
                <div class="question-container" id="question4">
                    <div class="question">
                        <div class="question-number">Question 4 of 15</div>
                        <div class="question-text">How does your skin react to new products?</div>
                        <div class="options">
                            <label class="option">
                                <input type="radio" name="react" value="easilyIrritated">
                                <span class="option-label">Easily irritated or red</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="react" value="sometimesIrritated">
                                <span class="option-label">Sometimes irritated</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="react" value="rarelyIrritated">
                                <span class="option-label">Rarely irritated</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="react" value="neverIrritated">
                                <span class="option-label">Never irritated</span>
                            </label>
                        </div>
                    </div>
                    <div class="navigation">
                        <button type="button" class="btn btn-secondary prev-btn">Previous</button>
                        <button type="button" class="btn btn-primary next-btn">Next</button>
                    </div>
                </div>
                
                <!-- Question 5 - Skin Concerns -->
                <div class="question-container" id="question5">
                    <div class="question">
                        <div class="question-number">Question 5 of 15</div>
                        <div class="question-text">What are your primary skin concerns? (Select all that apply)</div>
                        <div class="options">
                            <label class="option">
                                <input type="checkbox" name="concerns" value="acne">
                                <span class="option-label">Acne</span>
                            </label>
                            <label class="option">
                                <input type="checkbox" name="concerns" value="darkCircles">
                                <span class="option-label">Dark circles</span>
                            </label>
                            <label class="option">
                                <input type="checkbox" name="concerns" value="darkSpots">
                                <span class="option-label">Dark spots</span>
                            </label>
                            <label class="option">
                                <input type="checkbox" name="concerns" value="unevenTone">
                                <span class="option-label">Uneven skin tone</span>
                            </label>
                            <label class="option">
                                <input type="checkbox" name="concerns" value="fineLines">
                                <span class="option-label">Fine lines</span>
                            </label>
                            <label class="option">
                                <input type="checkbox" name="concerns" value="wrinkles">
                                <span class="option-label">Wrinkles</span>
                            </label>
                            <label class="option">
                                <input type="checkbox" name="concerns" value="roughSkin">
                                <span class="option-label">Rough skin</span>
                            </label>
                            <label class="option">
                                <input type="checkbox" name="concerns" value="chappedLips">
                                <span class="option-label">Chapped lips</span>
                            </label>
                            <label class="option">
                                <input type="checkbox" name="concerns" value="tanning">
                                <span class="option-label">Tanning</span>
                            </label>
                        </div>
                    </div>
                    <div class="navigation">
                        <button type="button" class="btn btn-secondary prev-btn">Previous</button>
                        <button type="button" class="btn btn-primary next-btn">Next</button>
                    </div>
                </div>
                
                <!-- Question 6 - Acne Severity -->
                <div class="question-container" id="question6">
                    <div class="question">
                        <div class="question-number">Question 6 of 15</div>
                        <div class="question-text">How severe is your acne?</div>
                        <div class="options">
                            <label class="option">
                                <input type="radio" name="acneSeverity" value="mild">
                                <span class="option-label">Mild (occasional pimples)</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="acneSeverity" value="moderate">
                                <span class="option-label">Moderate (regular breakouts)</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="acneSeverity" value="severe">
                                <span class="option-label">Severe (cystic acne)</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="acneSeverity" value="none">
                                <span class="option-label">I don't have acne</span>
                            </label>
                        </div>
                    </div>
                    <div class="navigation">
                        <button type="button" class="btn btn-secondary prev-btn">Previous</button>
                        <button type="button" class="btn btn-primary next-btn">Next</button>
                    </div>
                </div>
                
                <!-- Question 7 - Dark Circles -->
                <div class="question-container" id="question7">
                    <div class="question">
                        <div class="question-number">Question 7 of 15</div>
                        <div class="question-text">What do your dark circles look like?</div>
                        <div class="options">
                            <label class="option">
                                <input type="radio" name="darkCirclesType" value="bluePurple">
                                <span class="option-label">Blue or purple</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="darkCirclesType" value="brownBlack">
                                <span class="option-label">Brown or black</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="darkCirclesType" value="puffy">
                                <span class="option-label">Puffy and swollen</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="darkCirclesType" value="none">
                                <span class="option-label">I don't have dark circles</span>
                            </label>
                        </div>
                    </div>
                    <div class="navigation">
                        <button type="button" class="btn btn-secondary prev-btn">Previous</button>
                        <button type="button" class="btn btn-primary next-btn">Next</button>
                    </div>
                </div>
                
                <!-- Question 8 - Dark Spots Duration -->
                <div class="question-container" id="question8">
                    <div class="question">
                        <div class="question-number">Question 8 of 15</div>
                        <div class="question-text">How long have you had dark spots?</div>
                        <div class="options">
                            <label class="option">
                                <input type="radio" name="darkSpotsDuration" value="recent">
                                <span class="option-label">Recently appeared</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="darkSpotsDuration" value="months">
                                <span class="option-label">For several months</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="darkSpotsDuration" value="years">
                                <span class="option-label">For years</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="darkSpotsDuration" value="none">
                                <span class="option-label">I don't have dark spots</span>
                            </label>
                        </div>
                    </div>
                    <div class="navigation">
                        <button type="button" class="btn btn-secondary prev-btn">Previous</button>
                        <button type="button" class="btn btn-primary next-btn">Next</button>
                    </div>
                </div>
                
                <!-- Question 9 - Uneven Tone Areas -->
                <div class="question-container" id="question9">
                    <div class="question">
                        <div class="question-number">Question 9 of 15</div>
                        <div class="question-text">Which areas of your face have an uneven skin tone?</div>
                        <div class="options">
                            <label class="option">
                                <input type="radio" name="unevenToneAreas" value="forehead">
                                <span class="option-label">Forehead</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="unevenToneAreas" value="cheeks">
                                <span class="option-label">Cheeks</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="unevenToneAreas" value="mouth">
                                <span class="option-label">Around the mouth</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="unevenToneAreas" value="overall">
                                <span class="option-label">Overall face</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="unevenToneAreas" value="none">
                                <span class="option-label">I don't have uneven tone</span>
                            </label>
                        </div>
                    </div>
                    <div class="navigation">
                        <button type="button" class="btn btn-secondary prev-btn">Previous</button>
                        <button type="button" class="btn btn-primary next-btn">Next</button>
                    </div>
                </div>
                
                <!-- Question 10 - Fine Lines Location -->
                <div class="question-container" id="question10">
                    <div class="question">
                        <div class="question-number">Question 10 of 15</div>
                        <div class="question-text">Where do you notice fine lines and wrinkles?</div>
                        <div class="options">
                            <label class="option">
                                <input type="radio" name="fineLinesLocation" value="forehead">
                                <span class="option-label">Forehead</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="fineLinesLocation" value="eyes">
                                <span class="option-label">Around the eyes</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="fineLinesLocation" value="mouth">
                                <span class="option-label">Around the mouth</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="fineLinesLocation" value="overall">
                                <span class="option-label">Overall face</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="fineLinesLocation" value="none">
                                <span class="option-label">I don't have fine lines</span>
                            </label>
                        </div>
                    </div>
                    <div class="navigation">
                        <button type="button" class="btn btn-secondary prev-btn">Previous</button>
                        <button type="button" class="btn btn-primary next-btn">Next</button>
                    </div>
                </div>
                
                <!-- Question 11 - Rough Skin Frequency -->
                <div class="question-container" id="question11">
                    <div class="question">
                        <div class="question-number">Question 11 of 15</div>
                        <div class="question-text">How often do you experience rough or textured skin?</div>
                        <div class="options">
                            <label class="option">
                                <input type="radio" name="roughSkinFrequency" value="frequent">
                                <span class="option-label">Frequently</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="roughSkinFrequency" value="occasional">
                                <span class="option-label">Occasionally</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="roughSkinFrequency" value="rare">
                                <span class="option-label">Rarely</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="roughSkinFrequency" value="never">
                                <span class="option-label">Never</span>
                            </label>
                        </div>
                    </div>
                    <div class="navigation">
                        <button type="button" class="btn btn-secondary prev-btn">Previous</button>
                        <button type="button" class="btn btn-primary next-btn">Next</button>
                    </div>
                </div>
                
                <!-- Question 12 - Chapped Lips Frequency -->
                <div class="question-container" id="question12">
                    <div class="question">
                        <div class="question-number">Question 12 of 15</div>
                        <div class="question-text">How often do your lips feel chapped or dry?</div>
                        <div class="options">
                            <label class="option">
                                <input type="radio" name="chappedLipsFrequency" value="frequent">
                                <span class="option-label">Frequently</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="chappedLipsFrequency" value="occasional">
                                <span class="option-label">Occasionally</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="chappedLipsFrequency" value="rare">
                                <span class="option-label">Rarely</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="chappedLipsFrequency" value="never">
                                <span class="option-label">Never</span>
                            </label>
                        </div>
                    </div>
                    <div class="navigation">
                        <button type="button" class="btn btn-secondary prev-btn">Previous</button>
                        <button type="button" class="btn btn-primary next-btn">Next</button>
                    </div>
                </div>
                
                <!-- Question 13 - Tanning Frequency -->
                <div class="question-container" id="question13">
                    <div class="question">
                        <div class="question-number">Question 13 of 15</div>
                        <div class="question-text">How often are you exposed to the sun without protection?</div>
                        <div class="options">
                            <label class="option">
                                <input type="radio" name="tanningFrequency" value="frequent">
                                <span class="option-label">Frequently</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="tanningFrequency" value="occasional">
                                <span class="option-label">Occasionally</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="tanningFrequency" value="rare">
                                <span class="option-label">Rarely</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="tanningFrequency" value="never">
                                <span class="option-label">Never</span>
                            </label>
                        </div>
                    </div>
                    <div class="navigation">
                        <button type="button" class="btn btn-secondary prev-btn">Previous</button>
                        <button type="button" class="btn btn-primary next-btn">Next</button>
                    </div>
                </div>
                
                <!-- Question 14 - Water Intake -->
                <div class="question-container" id="question14">
                    <div class="question">
                        <div class="question-number">Question 14 of 15</div>
                        <div class="question-text">How much water do you drink daily?</div>
                        <div class="options">
                            <label class="option">
                                <input type="radio" name="waterIntake" value="less1">
                                <span class="option-label">Less than 1 liter</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="waterIntake" value="1to2">
                                <span class="option-label">1-2 liters</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="waterIntake" value="more2">
                                <span class="option-label">More than 2 liters</span>
                            </label>
                        </div>
                    </div>
                    <div class="navigation">
                        <button type="button" class="btn btn-secondary prev-btn">Previous</button>
                        <button type="button" class="btn btn-primary next-btn">Next</button>
                    </div>
                </div>
                
                <!-- Question 15 - Skincare Routine -->
                <div class="question-container" id="question15">
                    <div class="question">
                        <div class="question-number">Question 15 of 15</div>
                        <div class="question-text">Do you follow a skincare routine?</div>
                        <div class="options">
                            <label class="option">
                                <input type="radio" name="skincareRoutine" value="yes">
                                <span class="option-label">Yes, regularly</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="skincareRoutine" value="sometimes">
                                <span class="option-label">Sometimes</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="skincareRoutine" value="rarely">
                                <span class="option-label">Rarely</span>
                            </label>
                            <label class="option">
                                <input type="radio" name="skincareRoutine" value="never">
                                <span class="option-label">Never</span>
                            </label>
                        </div>
                    </div>
                    <div class="navigation">
                        <button type="button" class="btn btn-secondary prev-btn">Previous</button>
                        <button type="button" class="btn btn-primary" id="submitQuiz">Get Results</button>
                    </div>
                </div>
            </form>
        </div>
        
        <div class="result-container" id="resultContainer">
            <div class="result-header">
                <h2 class="result-title">Your Personalized Skin Analysis</h2>
                <p class="result-subtitle">Based on your answers, here's your comprehensive skin profile</p>
            </div>
            
            <div class="result-card">
                <h3 class="result-card-title">Skin Type</h3>
                <div class="result-content" id="skinTypeResult">
                    <!-- Will be filled by JavaScript -->
                </div>
            </div>
            
            <div class="result-card">
                <h3 class="result-card-title">Primary Concerns</h3>
                <div class="result-content" id="skinConcernsResult">
                    <!-- Will be filled by JavaScript -->
                </div>
            </div>
            
            <div class="result-card">
                <h3 class="result-card-title">Skin Health Score</h3>
                <div class="result-content" id="skinHealthResult">
                    <!-- Will be filled by JavaScript -->
                </div>
            </div>
            
            <div class="ebook-promo">
                <div class="ebook-promo-content">
                    <h3 class="ebook-title">Master The Art of Skincare</h3>
                    <p class="ebook-description">Discover the secrets to radiant, healthy skin with our comprehensive e-book. Packed with expert advice, personalized routines, and product recommendations, this guide will transform your skincare journey.</p>
                    <a href="https://payhip.com/theskincareguide" class="btn-ebook" target="_blank">Get Your E-book Now</a>
                </div>
            </div>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const totalQuestions = 15;
            let currentQuestion = 1;
            
            // Initialize progress bar
            updateProgressBar();
            
            // Next button functionality
            document.querySelectorAll('.next-btn').forEach(button => {
                button.addEventListener('click', function() {
                    if (validateQuestion(currentQuestion)) {
                        document.getElementById(`question${currentQuestion}`).classList.remove('active');
                        currentQuestion++;
                        document.getElementById(`question${currentQuestion}`).classList.add('active');
                        updateProgressBar();
                        
                        // Enable previous button after first question
                        if (currentQuestion > 1) {
                            document.querySelectorAll('.prev-btn').forEach(btn => {
                                btn.disabled = false;
                            });
                        }
                    }
                });
            });
            
            // Previous button functionality
            document.querySelectorAll('.prev-btn').forEach(button => {
                button.addEventListener('click', function() {
                    document.getElementById(`question${currentQuestion}`).classList.remove('active');
                    currentQuestion--;
                    document.getElementById(`question${currentQuestion}`).classList.add('active');
                    updateProgressBar();
                    
                    // Disable previous button on first question
                    if (currentQuestion === 1) {
                        document.querySelectorAll('.prev-btn').forEach(btn => {
                            btn.disabled = true;
                        });
                    }
                });
            });
            
            // Submit quiz
            document.getElementById('submitQuiz').addEventListener('click', function() {
                if (validateQuestion(currentQuestion)) {
                    calculateResult();
                    document.querySelector('.quiz-content').style.display = 'none';
                    document.getElementById('resultContainer').style.display = 'block';
                }
            });
            
            // Option selection styling
            document.querySelectorAll('.option input[type="radio"]').forEach(radio => {
                radio.addEventListener('change', function() {
                    // Remove selected class from all options in this question
                    const questionContainer = this.closest('.question-container');
                    questionContainer.querySelectorAll('.option').forEach(option => {
                        option.classList.remove('selected');
                    });
                    
                    // Add selected class to the parent label
                    if (this.checked) {
                        this.closest('.option').classList.add('selected');
                    }
                });
            });
            
            // For checkboxes
            document.querySelectorAll('.option input[type="checkbox"]').forEach(checkbox => {
                checkbox.addEventListener('change', function() {
                    if (this.checked) {
                        this.closest('.option').classList.add('selected');
                    } else {
                        this.closest('.option').classList.remove('selected');
                    }
                });
            });
            
            function updateProgressBar() {
                const progress = (currentQuestion / totalQuestions) * 100;
                document.getElementById('progressBar').style.width = `${progress}%`;
            }
            
            function validateQuestion(questionNum) {
                const questionContainer = document.getElementById(`question${questionNum}`);
                
                // For radio buttons
                const radioGroups = {};
                questionContainer.querySelectorAll('input[type="radio"]').forEach(radio => {
                    if (!radioGroups[radio.name]) {
                        radioGroups[radio.name] = false;
                    }
                    if (radio.checked) {
                        radioGroups[radio.name] = true;
                    }
                });
                
                // Check if any radio group is required but not selected
                for (const group in radioGroups) {
                    if (!radioGroups[group]) {
                        alert('Please select an option to continue.');
                        return false;
                    }
                }
                
                // For checkbox questions (like concerns)
                if (questionNum === 5) { // This is the concerns question
                    const checkedBoxes = questionContainer.querySelectorAll('input[type="checkbox"]:checked');
                    if (checkedBoxes.length === 0) {
                        alert('Please select at least one concern to continue.');
                        return false;
                    }
                }
                
                return true;
            }
            
            function calculateResult() {
                const form = document.forms['skinQuiz'];
                
                // Skin Type
                const skinType = form['skinFeel'].value;
                let skinTypeResult = '';
                if (skinType === 'oily') {
                    skinTypeResult = 'Your skin type is <span class="highlight">Oily</span>. You likely experience shine throughout the day and may be prone to breakouts. Look for oil-balancing products with ingredients like salicylic acid and niacinamide.';
                } else if (skinType === 'dry') {
                    skinTypeResult = 'Your skin type is <span class="highlight">Dry</span>. Your skin may feel tight or flaky and requires extra hydration. Seek out products with hyaluronic acid and ceramides to replenish moisture.';
                } else if (skinType === 'normal') {
                    skinTypeResult = 'Your skin type is <span class="highlight">Normal</span>. You have a good balance of oil and moisture. Maintain your skin health with a consistent routine and gentle products.';
                } else if (skinType === 'sensitive') {
                    skinTypeResult = 'Your skin type is <span class="highlight">Sensitive</span>. Your skin reacts easily to products or environmental factors. Focus on fragrance-free, soothing formulations with minimal ingredients.';
                }
                document.getElementById('skinTypeResult').innerHTML = skinTypeResult;
                
                // Skin Concerns
                const concerns = form['concerns'];
                let selectedConcerns = [];
                for (let concern of concerns) {
                    if (concern.checked) {
                        selectedConcerns.push(concern.nextElementSibling.textContent.trim());
                    }
                }
                document.getElementById('skinConcernsResult').innerHTML = `
                    <p>Your primary skin concerns are: <span class="highlight">${selectedConcerns.join(', ')}</span>.</p>
                    <p style="margin-top: 10px;">Discover how to address these concerns in our comprehensive e-book below.</p>
                `;
                
                // Skin Health Score
                const waterIntake = form['waterIntake']?.value || '1to2';
                const sleep = form['sleep']?.value || '5to7';
                const exercise = form['exercise']?.value || '1to2';
                const skincareRoutine = form['skincareRoutine']?.value || 'sometimes';
                
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
                
                const skinHealthPercentage = Math.min(100, Math.round((skinHealthScore / 40) * 100));
                
                let healthMessage = '';
                if (skinHealthPercentage >= 75) {
                    healthMessage = `Excellent! Your skin health score is <span class="highlight">${skinHealthPercentage}%</span>. You're taking great care of your skin with healthy habits. Keep up the good work and consider optimizing your routine with our expert guide.`;
                } else if (skinHealthPercentage >= 50) {
                    healthMessage = `Good! Your skin health score is <span class="highlight">${skinHealthPercentage}%</span>. You have some healthy habits in place, but there's room for improvement. Our guide can help you take your skincare to the next level.`;
                } else {
                    healthMessage = `Your skin health score is <span class="highlight">${skinHealthPercentage}%</span>. There are several opportunities to improve your skin's health through better hydration, sleep, and skincare habits. Our comprehensive guide can help you establish an effective routine.`;
                }
                
                document.getElementById('skinHealthResult').innerHTML = healthMessage;
            }
        });
    </script>
</body>
</html>
