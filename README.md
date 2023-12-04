<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>ProdigyIB Flashcards</title>
    <!-- Add a light blue background -->
    <style>
        body {
            background-color: #cfe4ff; /* Light blue background color */
            font-family: Arial, sans-serif; /* Choose a suitable font */
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            height: 100vh;
        }

        #flashcard-container {
            text-align: center;
            padding: 20px;
            background-color: #fff; /* White background for flashcard container */
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1); /* Add a subtle box shadow */
            margin-bottom: 20px;
            width: 80%; /* Utilize 80% of the available width */
        }

        #next-button, #reveal-button {
            background-color: #4CAF50; /* Green button color */
            color: #fff; /* White text color */
            padding: 10px 20px;
            font-size: 16px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            margin-right: 10px;
            margin-bottom: 10px; /* Increased margin */
        }

        #next-button:hover, #reveal-button:hover {
            background-color: #45a049; /* Darker green color on hover */
        }

        #title {
            font-size: 24px;
            font-weight: bold;
            margin-top: 20px;
            margin-bottom: 10px;
        }

        #description {
            font-size: 16px;
            text-align: center;
            margin-bottom: 20px;
            width: 80%; /* Utilize 80% of the available width */
        }

        #buttons-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
        }

    </style>

    <!-- linking to PyScript assets -->
    <link rel="stylesheet" href="https://pyscript.net/releases/2022.12.1/pyscript.css" />
    <script defer src="https://pyscript.net/releases/2022.12.1/pyscript.js"></script>
</head>
<body>
    <div id="title">ProdigyIB</div>
    <div id="description">Welcome to the ProdigyIB flashcard hub, an interactive and unique learning experience for IB students to learn and practice for their subjects!</div>

    <div id="flashcard-container">
        <!-- Flashcard content will be dynamically inserted here -->
    </div>

    <!-- Add "Next Flashcard" and "Reveal Answer" buttons -->
    <div id="buttons-container">
        <button id="next-button" onclick="generateFlashcard()">Next Flashcard</button>
        <button id="reveal-button" onclick="revealAnswer()">Reveal Answer</button>
    </div>

    <script>
        var currentQuestion;
        var currentAnswer;

        // Generate the first flashcard when the page loads
        window.onload = function () {
            generateFlashcard();
        };

        function generateFlashcard() {
            // Example flashcard data (replace with your actual data)
            var questions = [    "What is the square root of 36?",
    "Solve the equation 3x - 7 = 11.",
    "Who formulated the laws of motion?",
    "Name the scientist known for the theory of relativity.",
    "In which year did the Renaissance begin?",
    "Define the concept of 'supply and demand.'",
    "What is the formula for calculating the area of a triangle?",
    "Who wrote 'The Communist Manifesto'?",
    "What is the function of mitochondria in a cell?",
    "What is the chemical symbol for gold?",
    "Who is the author of 'Romeo and Juliet'?",
    "Name the largest planet in our solar system.",
    "What is the formula for kinetic energy?",
    "Who discovered penicillin?",
    "What is the capital of Japan?",
    "Define the term 'cognitive dissonance.'",
    "What is the process of converting water vapor into liquid water called?",
    "Name the first woman to win a Nobel Prize.",
    "What is the main function of the pancreas in the human body?",
    "Who developed the periodic table of elements?",
    "What is the formula for the area of a circle?",
    "Define the concept of 'gravity.'",
    "Name the famous scientist who developed the theory of evolution.",
    "What is the capital of Australia?",
    "Solve the quadratic equation 2x^2 - 5x + 3 = 0.",
    "Who is known as the 'Father of Modern Philosophy'?",
    "Define the term 'global warming.'",
    "What is the chemical symbol for water?",
    "Name the river that flows through Egypt.",
    "What is the capital of Brazil?",
    "Who is the founder of modern psychology?",
    "What is the primary function of red blood cells?",
    "Who discovered the electron?",
    "What is the formula for the volume of a cylinder?",
    "Define the concept of 'democracy.'",
    "What is the process of converting light energy into chemical energy in plants?",
    "Name the first woman in space.",
    "Who is the author of 'To Kill a Mockingbird'?",
    "What is the capital of South Africa?",
    "Define the term 'sociology.'",
    "Who proposed the theory of continental drift?",
    "What is the chemical symbol for oxygen?",
    "Name the scientist known for the theory of relativity.",
    "What is the capital of Italy?",
    "Who is considered the 'Father of Chemistry'?",
    "What is the formula for the perimeter of a rectangle?",
    "Define the term 'civil rights.'",
    "Define the concept of 'cultural relativism.'",
    "Name the political ideology advocating for classless and stateless society.",
    "What is the Magna Carta?",
    "Who is known as the 'Father of Economics'?",
    "What is the 'Declaration of Independence'?",
    "Define the term 'feminism.'",
    "Who wrote 'The Wealth of Nations'?",
    "Name the architect of the United Nations.",
    "What is the concept of 'checks and balances'?",
    "Who is the author of 'The Social Contract'?",
    "What is the 'Great Depression'?",
    "Define the term 'apartheid.'",
    "Name the first woman to win a Nobel Peace Prize.",
    "Who is the 'Iron Chancellor'?",
    "What is the 'Domesday Book'?",
    "Define the concept of 'human rights.'",
     "What is the value of the cube root of 64?",
    "Solve the equation 4x - 2 = 10.",
    "Find the integral of e^(2x) with respect to x.",
    "What is the value of e (Euler's number) to two decimal places?",
    "Evaluate the limit as x approaches 0 for sin(x)/x.",
    "Solve the quadratic equation 5x^2 - 3x - 2 = 0.",
    "Calculate the logarithm base 5 of 125.",
    "If a triangle has sides of length 7, 24, and 25, is it a right triangle?",
    "What is the surface area of a sphere with a radius of 8 units?",
    "Simplify the expression: (2/5)^3 ÷ (1/2)^2.",
    "If log base 3 of x is equal to 4, what is the value of x?",
    "Solve the inequality -2x + 7 > 3.",
    "What is the sum of the first 15 positive odd integers?",
    "If a rectangular prism has dimensions 4 cm by 6 cm by 10 cm, what is its volume?",
    "What is the probability of rolling an even number on a six-sided die?",
    "Solve the system of equations: 3x + 2y = 10 and 2x - y = 4.",
    "Find the derivative of f(x) = ln(x) with respect to x.",
    "What are the coordinates of the centroid of a triangle with vertices (0,0), (6,0), and (3,4)?",
    "If a train travels at a constant speed of 80 km/h, how far will it travel in 2.5 hours?",
    "Evaluate the expression: cos(60°) + tan(45°).",
     "Who developed the theory of general relativity?",
    "What is the chemical formula for methane?",
    "Describe the process of cell division in eukaryotic cells.",
    "Name the four fundamental forces in physics.",
    "Explain the function of the endoplasmic reticulum in a cell.",
    "State the law of conservation of energy.",
    "Who discovered the process of vaccination?",
    "What is the capital of Canada?",
    "Define the term 'psychology.'",
    "Name the elements in the halogen group of the periodic table.",
    "What is the formula for the circumference of a circle?",
    "Describe the process of mitosis.",
    "Who first proposed the idea of natural selection?",
    "What is the largest ocean on Earth?",
    "Define the term 'symbiosis.'",
    "What is the process of cellular respiration?",
    "Name the first satellite launched into space.",
    "What is the structure and function of ribosomes?",
    "Who discovered radioactivity?",
    "What is the formula for acceleration?",
     "Who wrote 'The Prince'?",
    "Explain the significance of the Renaissance.",
    "Name the leaders of the Allied Powers during World War II.",
    "What is the social contract theory?",
    "Define the term 'industrialization.'",
    "Who was the first President of the United States?",
    "What is the purpose of the United Nations?",
    "Who wrote 'The Communist Manifesto'?",
    "Describe the impact of the Columbian Exchange.",
    "What is the significance of the Emancipation Proclamation?",
    "Who was the first woman to receive a Ph.D. in psychology?",
    "Define the term 'imperialism.'",
    "Name the key figures of the Enlightenment.",
    "What is the significance of the Treaty of Versailles?",
    "Define the term 'urbanization.'",
    "Who was the leader of the Bolsheviks during the Russian Revolution?",
    "Explain the concept of cultural diffusion.",
    "What is the purpose of the World Health Organization?",
    "Who were the main contributors to the Declaration of Independence?",
    "Define the term 'Cold War.'",
     "Translate 'goodbye' into French.",
    "What is the French word for 'sun'?",
    "Give the French equivalent for 'please.'",
    "How do you say 'friend' in French?",
    "Translate 'to study' into French.",
    "What is the French word for 'beautiful'?",
    "What does 'au revoir' mean?",
    "How do you say 'I don't understand' in French?",
    "Translate 'book' into French.",
    "What is the French word for 'computer'?",
    "Give the French equivalent for 'excuse me.'",
    "How do you say 'family' in French?",
    "Translate 'to eat' into French.",
    "What is the French word for 'red'?",
    "What does 'merci beaucoup' mean?",
    "How do you say 'my name is' in French?",
    "Translate 'water' into French.",
    "What is the French word for 'cat'?",
    "Give the French equivalent for 'time.'",
    "Translate 'window' into Spanish.",
    "What is the Spanish word for 'tree'?",
    "Give the Spanish equivalent for 'good afternoon.'",
    "How do you say 'dog' in Spanish?",
    "Translate 'to dance' into Spanish.",
    "What is the Spanish word for 'happy'?",
    "What does 'adiós' mean?",
    "How do you say 'I don't know' in Spanish?",
    "Translate 'pencil' into Spanish.",
    "What is the Spanish word for 'phone'?",
    "Give the Spanish equivalent for 'please.'",
    "How do you say 'brother' in Spanish?",
    "Translate 'to read' into Spanish.",
    "What is the Spanish word for 'green'?",
    "What does 'gracias' mean?",
    "How do you say 'my name is' in Spanish?",
    "Translate 'water' into Spanish.",
    "What is the Spanish word for 'bird'?",
    "Give the Spanish equivalent for 'time.'",
    "Translate 'teacher' into German.",
    "What is the German word for 'sky'?",
    "Give the German equivalent for 'good night.'",
    "How do you say 'cat' in German?",
    "Translate 'to play' into German.",
    "What is the German word for 'big'?",
    "What does 'Auf Wiedersehen' mean?",
    "How do you say 'I don't understand' in German?",
    "Translate 'book' into German.",
    "What is the German word for 'computer'?",
    "Give the German equivalent for 'excuse me.'",
    "How do you say 'family' in German?",
    "Translate 'to drink' into German.",
    "What is the German word for 'yellow'?",
    "What does 'Danke schön' mean?",
    "How do you say 'my name is' in German?",
    "Translate 'water' into German.",
    "What is the German word for 'bird'?",
    "Give the German equivalent for 'time.'",];
            var answers = ["6",
    "x = 6",
    "Isaac Newton",
    "Albert Einstein",
    "14th century",
    "The economic model of determining the price of goods and services.",
    "Area = (1/2) * base * height",
    "Karl Marx",
    "Powerhouse of the cell; produces energy.",
    "Au",
    "William Shakespeare",
    "Jupiter",
    "KE = (1/2) * mass * velocity^2",
    "Alexander Fleming",
    "Tokyo",
    "The discomfort experienced when holding two conflicting beliefs.",
    "Condensation",
    "Marie Curie",
    "Regulates blood sugar levels and aids in digestion.",
    "Dmitri Mendeleev",
    "Area = π * radius^2",
    "The force that attracts objects toward each other.",
    "Charles Darwin",
    "Canberra",
    "x = 1 or x = 3/2",
    "René Descartes",
    "The increase in Earth's average surface temperature.",
    "H2O",
    "Nile",
    "Brasília",
    "Wilhelm Wundt",
    "Oxygen transport to tissues.",
    "J.J. Thomson",
    "Volume = π * radius^2 * height",
    "A system of government by the whole population.",
    "Photosynthesis",
    "Valentina Tereshkova",
    "Harper Lee",
    "Pretoria",
    "The study of society and human social behavior.",
    "Alfred Wegener",
    "O2",
    "Albert Einstein",
    "Rome",
    "Antoine Lavoisier",
    "Perimeter = 2 * (length + width)",
    "The rights of citizens to political and social freedom.",
    "The idea that all cultural beliefs are equally valid.",
    "Anarchism",
    "A historic document limiting the powers of the monarchy.",
    "Adam Smith",
    "A declaration asserting the independence of a nation.",
    "Advocacy for the rights and equality of women.",
    "Adam Smith",
    "Sir Norman Foster",
    "A system to prevent the concentration of power.",
    "Jean-Jacques Rousseau",
    "A severe worldwide economic downturn in the 1930s.",
    "A policy of racial segregation and discrimination.",
    "Jane Addams",
    "Otto von Bismarck",
    "A record of property ownership in medieval England.",
    "The fundamental rights and freedoms inherent to all humans.",
     "4",
    "x = 3",
    "(1/2)e^(2x) + C",
    "2.71",
    "1",
    "x = -1 or x = 0.4",
    "3",
    "Yes",
    "804.25 square units",
    "1/2",
    "64",
    "x < 2",
    "225",
    "240 cm^3",
    "1/2",
    "x = 2, y = 2",
    "1/x",
    "(3, 2)",
    "200 km",
    "√3 + 1",
    "Albert Einstein",
    "CH₄",
    "It involves the division of the nucleus and then the cytoplasm.",
    "Gravity, electromagnetism, weak nuclear force, strong nuclear force.",
    "It is involved in protein synthesis and lipid metabolism.",
    "Energy cannot be created or destroyed, only transformed.",
    "Edward Jenner",
    "Ottawa",
    "The scientific study of the mind and behavior.",
    "Fluorine, chlorine, bromine, iodine, astatine.",
    "C = 2πr",
    "It is the division of a cell into two identical daughter cells.",
    "Charles Darwin",
    "Pacific Ocean",
    "A close and long-term interaction between different biological species.",
    "It involves the breakdown of glucose to produce ATP and CO₂.",
    "Sputnik 1",
    "They are cellular structures involved in protein synthesis.",
    "Marie Curie",
    "a = (v - u) / t",
    "Niccolò Machiavelli",
    "It marked the rebirth of art, culture, and learning in Europe.",
    "Franklin D. Roosevelt, Winston Churchill, Joseph Stalin.",
    "It is the idea that individuals give up some freedoms for the protection of others.",
    "The process by which an economy shifts from agrarian and handicraft industries to industrial and machine-based industries.",
    "George Washington",
    "To promote international cooperation and prevent conflicts.",
    "Karl Marx and Friedrich Engels",
    "It facilitated the exchange of crops, animals, and diseases between the Old and New Worlds.",
    "It declared all slaves in Confederate-held territory to be free.",
    "Mary Whiton Calkins",
    "A policy of extending a country's power and influence through diplomacy or military force.",
    "Voltaire, John Locke, Montesquieu, Rousseau.",
    "It imposed severe penalties on Germany and is considered a contributing factor to World War II.",
    "The process of population shift from rural to urban areas.",
    "Vladimir Lenin",
    "The spread of cultural elements from one society to another.",
    "To direct international health within the United Nations' system.",
    "Thomas Jefferson, Benjamin Franklin, John Adams.",
    "A state of political tension and military rivalry between nations that stops short of full-scale war.",
    "Au revoir",
    "Soleil",
    "S'il vous plaît",
    "Ami / Amie",
    "Étudier",
    "Beau / Belle",
    "Goodbye",
    "Je ne comprends pas",
    "Livre",
    "Ordinateur",
    "Excusez-moi",
    "Famille",
    "Manger",
    "Rouge",
    "Thank you very much",
    "Je m'appelle",
    "Eau",
    "Chat",
    "Temps",
    "Ventana",
    "Árbol",
    "Buenas tardes",
    "Perro",
    "Bailar",
    "Feliz",
    "Goodbye",
    "No sé",
    "Lápiz",
    "Teléfono",
    "Por favor",
    "Hermano",
    "Leer",
    "Verde",
    "Thank you",
    "Me llamo",
    "Agua",
    "Pájaro",
    "Tiempo",
    "Lehrer / Lehrerin",
    "Himmel",
    "Gute Nacht",
    "Katze",
    "Spielen",
    "Groß",
    "Goodbye",
    "Ich verstehe nicht",
    "Buch",
    "Computer",
    "Entschuldigen Sie",
    "Familie",
    "Trinken",
    "Gelb",
    "Thank you very much",
    "Ich heiße",
    "Wasser",
    "Vogel",
    "Zeit",
];

            // Selecting a random index from the list of questions/answers
            var randomIndex = Math.floor(Math.random() * questions.length);

            // Getting the question and answer at the random index
            currentQuestion = questions[randomIndex];
            currentAnswer = answers[randomIndex];

            // Display the question
            document.querySelector('#flashcard-container').innerHTML = "<p>Flashcard:</p><p>Question: " + currentQuestion + "</p>";

            // Clear previous answer
            var previousAnswer = document.querySelector('#flashcard-container #answer');
            if (previousAnswer) {
                previousAnswer.remove();
            }
        }

        function revealAnswer() {
            // Create a new answer element
            var answerElement = document.createElement('p');
            answerElement.id = 'answer';
            answerElement.innerHTML = "Answer: " + currentAnswer;

            // Display the answer
            document.querySelector('#flashcard-container').appendChild(answerElement);
        }
    </script>
</body>
</html>
