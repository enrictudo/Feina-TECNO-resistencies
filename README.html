<!DOCTYPE html>
<html lang="ca">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora i Exercicis de Resistències</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* Configuració del viewport i font */
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');
        body {
            font-family: 'Inter', sans-serif;
            background-color: #111827; /* Fons molt fosc */
            color: #e5e7eb; /* Text clar */
        }

        .container-section {
            background-color: #1f2937; /* Gris fosc per a seccions */
            border-radius: 12px;
            padding: 32px;
            margin-bottom: 40px;
            box-shadow: 0 10px 15px rgba(0, 0, 0, 0.3);
        }

        /* Estil per al resistor visual */
        .resistor-body {
            height: 40px;
            background-color: #8b6b3e; /* Marró mig fosc per contrast */
            border-radius: 6px;
            position: relative;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.6);
            flex-shrink: 0; /* Ensures it maintains its size */
            width: 45%; /* Relative width within the visual container */
        }

        .resistor-band {
            position: absolute;
            height: 100%;
            width: 12px;
            box-shadow: inset 0 0 5px rgba(0, 0, 0, 0.6);
            border-radius: 3px;
        }

        /* Posicionament de les 4 bandes */
        .band-1 { left: 12%; }
        .band-2 { left: 32%; }
        .band-3 { left: 52%; }
        .band-4 { right: 12%; } /* Tolerance band is separated */
        
        .resistor-lead {
            height: 4px;
            background-color: #a0a0a0; /* Gris metàl·lic */
            flex-grow: 1; /* Leads fill remaining space */
        }

        /* Ajust per a selecció de colors en mode fosc */
        select option {
            background-color: #374151;
            color: #e5e7eb;
        }
        .bg-gray-700-custom {
            background-color: #374151; /* Darker background for elements */
        }
    </style>
    <script>
        // Taula de dades dels colors del resistor
        const RESISTOR_COLORS = {
            "Negre": [0, 0, 1, null, "#222222", "B1/B2"],
            "Marró": [1, 1, 10, 1, "#964B00", "B1/B2/Mult/Tol"],
            "Vermell": [2, 2, 100, 2, "#FF0000", "B1/B2/Mult/Tol"],
            "Taronja": [3, 3, 1000, null, "#FF9900", "B1/B2/Mult"],
            "Groc": [4, 4, 10000, null, "#FFFF00", "B1/B2/Mult"],
            "Verd": [5, 5, 100000, 0.5, "#00AA00", "B1/B2/Mult/Tol"],
            "Blau": [6, 6, 1000000, 0.25, "#0000FF", "B1/B2/Mult/Tol"],
            "Violeta": [7, 7, 10000000, 0.1, "#8A2BE2", "B1/B2/Mult/Tol"],
            "Gris": [8, 8, 100000000, 0.05, "#808080", "B1/B2/Mult/Tol"],
            "Blanc": [9, 9, 1000000000, null, "#FFFFFF", "B1/B2/Mult"],
            "Or": [null, null, 0.1, 5, "#FFD700", "Mult/Tol"],
            "Plata": [null, null, 0.01, 10, "#C0C0C0", "Mult/Tol"],
            "Sense color": [null, null, null, 20, "transparent", "Tol"],
            "Cap": [null, null, null, null, "transparent", "None"]
        };

        // Map d'índexs a l'array de dades (corregit per evitar col·lisions)
        const COLOR_INDICES = {
            SIGNIFICATIVE: 0,
            MULTIPLIER: 2,
            TOLERANCE: 3,
            HEX: 4,
            USES: 5
        };

        let currentExercise = null; // Per mantenir l'estat de l'exercici
        let currentProblemType = 'C2V';

        // --- Funcions de Formatació ---

        /** Funció per obtenir un element aleatori d'un array */
        function getRandomElement(arr) {
            return arr[Math.floor(Math.random() * arr.length)];
        }

        /** Funció per formatar la resistència amb unitats (Ohm, kOhm, MOhm) */
        function formatResistance(value) {
            if (value >= 1000000) return (value / 1000000).toFixed(2).replace(/\.?0+$/, '') + " M$\\Omega$";
            if (value >= 1000) return (value / 1000).toFixed(2).replace(/\.?0+$/, '') + " k$\\Omega$";
            return value.toFixed(2).replace(/\.?0+$/, '') + " $\\Omega$";
        }
        
        // --- Funcions de Càlcul de Base ---
        
        /** Funció per obtenir les opcions de colors vàlides per a una banda */
        function getBandOptions(bandName) {
            let allowedUses = [];
            switch (bandName) {
                case 'band1': allowedUses = ['B1/B2', 'B1/B2/Mult', 'B1/B2/Mult/Tol']; break;
                case 'band2': allowedUses = ['B1/B2', 'B1/B2/Mult', 'B1/B2/Mult/Tol']; break;
                case 'band3': allowedUses = ['B1/B2/Mult', 'B1/B2/Mult/Tol', 'Mult/Tol']; break;
                case 'band4': allowedUses = ['B1/B2/Mult/Tol', 'Mult/Tol', 'Tol']; break;
            }

            return Object.keys(RESISTOR_COLORS).filter(color => {
                const uses = RESISTOR_COLORS[color][COLOR_INDICES.USES];
                return allowedUses.some(allowed => uses.includes(allowed));
            });
        }

        // --- Lògica: Visualització ---

        function updateResistorVisual(bands) {
            const bandsContainer = document.querySelectorAll('.resistor-visual-container');
            
            bandsContainer.forEach(container => {
                container.querySelector('#vis-band-1').style.backgroundColor = RESISTOR_COLORS[bands[0]][COLOR_INDICES.HEX];
                container.querySelector('#vis-band-2').style.backgroundColor = RESISTOR_COLORS[bands[1]][COLOR_INDICES.HEX];
                container.querySelector('#vis-band-3').style.backgroundColor = RESISTOR_COLORS[bands[2]][COLOR_INDICES.HEX];
                
                const tolColor = RESISTOR_COLORS[bands[3]][COLOR_INDICES.HEX];
                const band4 = container.querySelector('#vis-band-4');
                
                // Si és "Sense color" o "Cap", mostrem l'interior del resistor amb un contorn discontinu
                band4.style.backgroundColor = (tolColor === 'transparent') ? 'transparent' : tolColor; 
                band4.style.border = (tolColor === 'transparent') ? '2px dashed #4b5563' : 'none'; // Gris fosc discontinu
            });
        }

        // --- Lògica: Colors a Valor (C->V) ---

        function calculateColorsToValue() {
            const b1Color = document.getElementById('b1-select').value;
            const b2Color = document.getElementById('b2-select').value;
            const b3Color = document.getElementById('b3-select').value;
            const b4Color = document.getElementById('b4-select').value;

            // Només actualitzar el visual de la secció C->V
            const visualContainer = document.getElementById('cv-resistor-visual');
            visualContainer.querySelector('#vis-band-1').style.backgroundColor = RESISTOR_COLORS[b1Color][COLOR_INDICES.HEX];
            visualContainer.querySelector('#vis-band-2').style.backgroundColor = RESISTOR_COLORS[b2Color][COLOR_INDICES.HEX];
            visualContainer.querySelector('#vis-band-3').style.backgroundColor = RESISTOR_COLORS[b3Color][COLOR_INDICES.HEX];
            
            const tolColor = RESISTOR_COLORS[b4Color][COLOR_INDICES.HEX];
            const band4 = visualContainer.querySelector('#vis-band-4');
            band4.style.backgroundColor = (tolColor === 'transparent') ? 'transparent' : tolColor; 
            band4.style.border = (tolColor === 'transparent') ? '2px dashed #4b5563' : 'none';

            const b1Value = RESISTOR_COLORS[b1Color][COLOR_INDICES.SIGNIFICATIVE];
            const b2Value = RESISTOR_COLORS[b2Color][COLOR_INDICES.SIGNIFICATIVE];
            const multiplier = RESISTOR_COLORS[b3Color][COLOR_INDICES.MULTIPLIER];
            const tolerance = RESISTOR_COLORS[b4Color][COLOR_INDICES.TOLERANCE];

            const resultDiv = document.getElementById('colors-to-value-result');
            resultDiv.innerHTML = '';
            resultDiv.classList.remove('bg-red-900', 'border-red-500');
            resultDiv.classList.add('bg-gray-700-custom', 'border-blue-500');


            if (b1Value === null || b2Value === null || multiplier === null || tolerance === null) {
                resultDiv.innerHTML = `<p class="text-red-300 font-semibold">Error de càlcul: Assegura't de seleccionar colors vàlids (ex. El negre no pot ser B1, 'Sense color' no pot ser multiplicador).<p>`;
                resultDiv.classList.replace('bg-gray-700-custom', 'bg-red-900');
                resultDiv.classList.add('border-red-500');
                return;
            }

            const nominalValue = (b1Value * 10 + b2Value) * multiplier;
            const toleranceP = tolerance;
            const max = nominalValue * (1 + toleranceP / 100);
            const min = nominalValue * (1 - toleranceP / 100);

            resultDiv.innerHTML = `
                <p class="text-lg font-semibold mb-2 text-blue-300">Resultats del Codi de Colors:</p>
                <div class="space-y-1">
                    <p><strong>Valor Nominal:</strong> <span class="text-xl font-bold text-green-400">${formatResistance(nominalValue)}</span></p>
                    <p><strong>Tolerància:</strong> $\\pm ${toleranceP}\\%$ (${b4Color})</p>
                    <p><strong>Valor Màxim:</strong> ${formatResistance(max)}</p>
                    <p><strong>Valor Mínim:</strong> ${formatResistance(min)}</p>
                    <p class="mt-3 text-sm text-gray-400">El valor real del resistor es troba entre ${formatResistance(min)} i ${formatResistance(max)}.</p>
                </div>
            `;
            if (window.MathJax) window.MathJax.typesetPromise();
        }

        // --- Lògica: Valor a Colors (V->C) ---

        const TOLERANCE_MAP = {};
        Object.entries(RESISTOR_COLORS).forEach(([color, data]) => {
            if (data[COLOR_INDICES.TOLERANCE] !== null) {
                TOLERANCE_MAP[data[COLOR_INDICES.TOLERANCE]] = color;
            }
        });

        function calculateValueToColors() {
            const nominalInput = document.getElementById('nominal-value-input').value;
            const toleranceInput = document.getElementById('tolerance-select').value;
            const resultDiv = document.getElementById('value-to-colors-result');

            // Només actualitzar el visual de la secció V->C
            const visualContainer = document.getElementById('vc-resistor-visual');

            resultDiv.innerHTML = '';
            resultDiv.classList.remove('bg-red-900', 'border-red-500');
            resultDiv.classList.add('bg-gray-700-custom', 'border-green-500');

            const R = parseFloat(nominalInput);
            const T = parseFloat(toleranceInput);

            if (isNaN(R) || R <= 0 || isNaN(T)) {
                // Reinicia visual en cas d'error
                updateVisualFromBands(visualContainer, ["Cap", "Cap", "Cap", "Cap"]);
                resultDiv.innerHTML = `<p class="text-red-300 font-semibold">Si us plau, introdueix un valor nominal vàlid (major que 0) i selecciona una tolerància.</p>`;
                resultDiv.classList.replace('bg-gray-700-custom', 'bg-red-900');
                resultDiv.classList.add('border-red-500');
                return;
            }

            const b4Color = TOLERANCE_MAP[T];
            let b3Color = null;
            let R_normalized = null;
            let multiplierValue = null;

            const multipliers = Object.entries(RESISTOR_COLORS)
                .map(([color, data]) => ({ color, value: data[COLOR_INDICES.MULTIPLIER] }))
                .filter(m => m.value !== null)
                .sort((a, b) => b.value - a.value);

            for (const { color, value } of multipliers) {
                const normalized = R / value;
                // Comprovem si el valor normalitzat està entre 10 i 99
                if (normalized >= 10 && normalized < 100 && (Math.abs(normalized - Math.round(normalized)) < 0.00000001 || normalized < 99.99)) {
                    b3Color = color;
                    multiplierValue = value;
                    R_normalized = normalized;
                    break;
                }
            }

            if (b3Color === null) {
                updateVisualFromBands(visualContainer, ["Cap", "Cap", "Cap", "Cap"]);
                resultDiv.innerHTML = `<p class="text-red-300 font-semibold">No es pot trobar un codi de color estàndard de 4 bandes per a ${formatResistance(R)}. Prova amb un valor arrodonit o amb un nombre diferent de xifres significatives (entre 10 i 99).<p>`;
                resultDiv.classList.replace('bg-gray-700-custom', 'bg-red-900');
                resultDiv.classList.add('border-red-500');
                if (window.MathJax) window.MathJax.typesetPromise();
                return;
            }

            const d1 = Math.floor(R_normalized / 10);
            const d2 = Math.round(R_normalized % 10);

            const b1Color = Object.keys(RESISTOR_COLORS).find(k => RESISTOR_COLORS[k][COLOR_INDICES.SIGNIFICATIVE] === d1 && RESISTOR_COLORS[k][COLOR_INDICES.SIGNIFICATIVE] !== null);
            const b2Color = Object.keys(RESISTOR_COLORS).find(k => RESISTOR_COLORS[k][COLOR_INDICES.SIGNIFICATIVE] === d2 && RESISTOR_COLORS[k][COLOR_INDICES.SIGNIFICATIVE] !== null);

            if (!b1Color || !b2Color) {
                updateVisualFromBands(visualContainer, ["Cap", "Cap", "Cap", "Cap"]);
                 resultDiv.innerHTML = `<p class="text-red-300 font-semibold">Error intern: No s'han trobat colors per als dígits ${d1} i ${d2}.</p>`;
                resultDiv.classList.replace('bg-gray-700-custom', 'bg-red-900');
                resultDiv.classList.add('border-red-500');
                if (window.MathJax) window.MathJax.typesetPromise();
                return;
            }

            updateVisualFromBands(visualContainer, [b1Color, b2Color, b3Color, b4Color]);

            resultDiv.innerHTML = `
                <p class="text-lg font-semibold mb-2 text-blue-300">Codi de Colors Requerit:</p>
                <div class="space-y-2">
                    <p><strong>Banda 1 (1a Xifra):</strong> <span class="font-bold" style="color: ${RESISTOR_COLORS[b1Color][COLOR_INDICES.HEX]}">${b1Color}</span> (${d1})</p>
                    <p><strong>Banda 2 (2a Xifra):</strong> <span class="font-bold" style="color: ${RESISTOR_COLORS[b2Color][COLOR_INDICES.HEX]}">${b2Color}</span> (${d2})</p>
                    <p><strong>Banda 3 (Multiplicador):</strong> <span class="font-bold" style="color: ${RESISTOR_COLORS[b3Color][COLOR_INDICES.HEX]}">${b3Color}</span> ($\times ${multiplierValue}$)</p>
                    <p><strong>Banda 4 (Tolerància):</strong> <span class="font-bold" style="color: ${RESISTOR_COLORS[b4Color][COLOR_INDICES.HEX]}">${b4Color}</span> ($\pm ${T}\\%$)</p>
                </div>
                <p class="mt-4 text-sm text-gray-400">Aquest és el codi de 4 bandes més proper per al valor ${formatResistance(R)} amb $\\pm ${T}\\%$ de tolerància.</p>
            `;
            if (window.MathJax) window.MathJax.typesetPromise();
        }

        // --- Funcions d'Exercicis Interactius ---
        
        function updateVisualFromBands(container, bands) {
            container.querySelector('#vis-band-1').style.backgroundColor = RESISTOR_COLORS[bands[0]][COLOR_INDICES.HEX];
            container.querySelector('#vis-band-2').style.backgroundColor = RESISTOR_COLORS[bands[1]][COLOR_INDICES.HEX];
            container.querySelector('#vis-band-3').style.backgroundColor = RESISTOR_COLORS[bands[2]][COLOR_INDICES.HEX];
            
            const tolColor = RESISTOR_COLORS[bands[3]][COLOR_INDICES.HEX];
            const band4 = container.querySelector('#vis-band-4');
            band4.style.backgroundColor = (tolColor === 'transparent') ? 'transparent' : tolColor; 
            band4.style.border = (tolColor === 'transparent') ? '2px dashed #4b5563' : 'none';
        }

        function generateRandomProblem() {
            // 1. D1 (1-9), D2 (0-9)
            const d1 = Math.floor(Math.random() * 9) + 1; 
            const d2 = Math.floor(Math.random() * 10);
            const significativeValue = d1 * 10 + d2;
            
            // 2. Multiplier (preferir multiplicadors que no siguin Or/Plata per a major varietat)
            const validMultipliers = Object.keys(RESISTOR_COLORS).filter(c => RESISTOR_COLORS[c][COLOR_INDICES.MULTIPLIER] !== null);
            let multiplierColor = getRandomElement(validMultipliers.filter(c => !['Or', 'Plata'].includes(c)));
            
            // Si el valor significatiu és baix (10-19), permetre Or/Plata com a multiplicador (més comú en valors petits)
            if (significativeValue < 20 && Math.random() < 0.3) {
                 multiplierColor = getRandomElement(validMultipliers);
            }

            const multiplierValue = RESISTOR_COLORS[multiplierColor][COLOR_INDICES.MULTIPLIER];
            
            // 3. Tolerance (tots els que tinguin tolerància, sense "Sense color" per a exercicis clars)
            const validTolerances = Object.keys(RESISTOR_COLORS).filter(c => RESISTOR_COLORS[c][COLOR_INDICES.TOLERANCE] !== null && c !== 'Sense color');
            const toleranceColor = getRandomElement(validTolerances);
            const toleranceValue = RESISTOR_COLORS[toleranceColor][COLOR_INDICES.TOLERANCE];

            const nominalValue = significativeValue * multiplierValue;
            
            const b1Color = Object.keys(RESISTOR_COLORS).find(k => RESISTOR_COLORS[k][COLOR_INDICES.SIGNIFICATIVE] === d1);
            const b2Color = Object.keys(RESISTOR_COLORS).find(k => RESISTOR_COLORS[k][COLOR_INDICES.SIGNIFICATIVE] === d2);
            
            currentExercise = {
                type: currentProblemType,
                bands: [b1Color, b2Color, multiplierColor, toleranceColor],
                nominal: nominalValue,
                toleranceP: toleranceValue
            };
            
            renderExercise();
        }

        function createExerciseSelect(id, bandName, initialColor) {
            const select = document.createElement('select');
            select.id = id;
            select.className = "w-full p-2 border border-gray-600 rounded-lg focus:ring-blue-500 focus:border-blue-500 bg-gray-700-custom text-gray-200 shadow-sm";

            let options = getBandOptions(bandName);
            
            // Filtres específics per a les bandes de l'exercici (no volem 'Sense color' ni 'Cap' com a opció de resposta)
            const finalOptions = (bandName === 'band4') 
                ? options.filter(c => RESISTOR_COLORS[c][COLOR_INDICES.TOLERANCE] !== null && c !== 'Sense color' && c !== 'Cap') 
                : options.filter(c => RESISTOR_COLORS[c][COLOR_INDICES.SIGNIFICATIVE] !== null && c !== 'Cap');
            
            // Afegim una opció inicial 'Selecciona...'
             const placeholder = document.createElement('option');
            placeholder.value = "";
            placeholder.textContent = "— Selecciona un color —";
            placeholder.disabled = true;
            placeholder.selected = true;
            select.appendChild(placeholder);


            finalOptions.forEach(color => {
                const option = document.createElement('option');
                option.value = color;
                option.textContent = color;
                option.style.backgroundColor = RESISTOR_COLORS[color][COLOR_INDICES.HEX];
                option.style.color = (color === "Blanc" || color === "Groc" || color === "Or" || color === "Plata") ? '#000' : '#FFF';
                select.appendChild(option);
            });

            return select;
        }

        function renderExercise() {
            const problemDiv = document.getElementById('exercise-problem-display');
            const inputDiv = document.getElementById('exercise-input-fields');
            const feedbackDiv = document.getElementById('exercise-feedback');
            const visualContainer = document.getElementById('ex-resistor-visual');

            feedbackDiv.innerHTML = '';
            feedbackDiv.classList.add('hidden');
            
            document.getElementById('next-exercise-btn').classList.add('hidden');
            document.getElementById('check-exercise-btn').classList.remove('hidden');

            
            if (currentExercise.type === 'C2V') {
                updateVisualFromBands(visualContainer, currentExercise.bands);

                problemDiv.innerHTML = `
                    <p class="text-lg mb-4 text-gray-200">Determina el valor nominal i la tolerància d'aquest resistor. Les seves bandes són:</p>
                    <div class="grid grid-cols-2 sm:grid-cols-4 gap-2 text-sm font-semibold text-center">
                        <span class="p-2 rounded-lg bg-gray-700-custom border border-gray-600">B1: <span style="color: ${RESISTOR_COLORS[currentExercise.bands[0]][COLOR_INDICES.HEX]}">${currentExercise.bands[0]}</span></span>
                        <span class="p-2 rounded-lg bg-gray-700-custom border border-gray-600">B2: <span style="color: ${RESISTOR_COLORS[currentExercise.bands[1]][COLOR_INDICES.HEX]}">${currentExercise.bands[1]}</span></span>
                        <span class="p-2 rounded-lg bg-gray-700-custom border border-gray-600">Mult: <span style="color: ${RESISTOR_COLORS[currentExercise.bands[2]][COLOR_INDICES.HEX]}">${currentExercise.bands[2]}</span></span>
                        <span class="p-2 rounded-lg bg-gray-700-custom border border-gray-600">Tol: <span style="color: ${RESISTOR_COLORS[currentExercise.bands[3]][COLOR_INDICES.HEX]}">${currentExercise.bands[3]}</span></span>
                    </div>
                `;
                inputDiv.innerHTML = `
                    <div class="grid grid-cols-2 gap-4">
                        <div>
                            <label class="block text-sm font-medium text-gray-300 mb-1">Valor Nominal ($\Omega$)</label>
                            <input type="number" id="ex-nominal-input" placeholder="Ohm" step="any" class="w-full p-2 border border-gray-600 rounded-lg focus:ring-blue-500 focus:border-blue-500 bg-gray-700-custom text-gray-200 shadow-sm" autocomplete="off">
                        </div>
                        <div>
                            <label class="block text-sm font-medium text-gray-300 mb-1">Tolerància (%)</label>
                            <input type="number" id="ex-tolerance-input" placeholder="%" step="any" class="w-full p-2 border border-gray-600 rounded-lg focus:ring-blue-500 focus:border-blue-500 bg-gray-700-custom text-gray-200 shadow-sm" autocomplete="off">
                        </div>
                    </div>
                `;
            } else {
                // V2C
                updateVisualFromBands(visualContainer, ["Cap", "Cap", "Cap", "Cap"]); // Resistor buit
                const R_display = formatResistance(currentExercise.nominal);
                
                problemDiv.innerHTML = `
                    <p class="text-lg mb-4 text-gray-200">Quin és el codi de colors per a un resistor de **${R_display}** amb una tolerància de **$\\pm ${currentExercise.toleranceP}\\%$**?</p>
                `;
                inputDiv.innerHTML = `
                    <div class="grid grid-cols-2 sm:grid-cols-4 gap-4">
                        <div>
                            <label class="block text-sm font-medium text-gray-300 mb-1">Banda 1</label>
                            <div id="ex-b1-select-container"></div>
                        </div>
                        <div>
                            <label class="block text-sm font-medium text-gray-300 mb-1">Banda 2</label>
                            <div id="ex-b2-select-container"></div>
                        </div>
                        <div>
                            <label class="block text-sm font-medium text-gray-300 mb-1">Banda 3 (Mult.)</label>
                            <div id="ex-b3-select-container"></div>
                        </div>
                        <div>
                            <label class="block text-sm font-medium text-gray-300 mb-1">Banda 4 (Tol.)</label>
                            <div id="ex-b4-select-container"></div>
                        </div>
                    </div>
                `;
                document.getElementById('ex-b1-select-container').appendChild(createExerciseSelect('ex-b1-select', 'band1', null));
                document.getElementById('ex-b2-select-container').appendChild(createExerciseSelect('ex-b2-select', 'band2', null));
                document.getElementById('ex-b3-select-container').appendChild(createExerciseSelect('ex-b3-select', 'band3', null));
                document.getElementById('ex-b4-select-container').appendChild(createExerciseSelect('ex-b4-select', 'band4', null));
            }
            
            if (window.MathJax) window.MathJax.typesetPromise();
        }

        function checkExerciseSolution() {
            const feedbackDiv = document.getElementById('exercise-feedback');
            feedbackDiv.classList.remove('hidden', 'bg-green-700', 'bg-red-700', 'bg-red-900', 'bg-green-900');
            
            let isCorrect = false;
            let message = '';
            
            if (!currentExercise) return;
            
            if (currentExercise.type === 'C2V') {
                const nominalInput = parseFloat(document.getElementById('ex-nominal-input').value);
                const toleranceInput = parseFloat(document.getElementById('ex-tolerance-input').value);
                
                const nominalTarget = currentExercise.nominal;
                const toleranceTarget = currentExercise.toleranceP;

                // Utilitzem una petita tolerància per a la comparació de nombres flotants
                const nominalIsCorrect = Math.abs(nominalInput - nominalTarget) < 0.01;
                const toleranceIsCorrect = Math.abs(toleranceInput - toleranceTarget) < 0.01;

                document.getElementById('ex-nominal-input').disabled = true;
                document.getElementById('ex-tolerance-input').disabled = true;

                if (nominalIsCorrect && toleranceIsCorrect) {
                    isCorrect = true;
                    message = `Molt bé! Els càlculs són perfectes. Valor Nominal Correcte: ${formatResistance(nominalTarget)}, Tolerància: $\\pm ${toleranceTarget}\\%$.`;
                } else {
                    message = `
                        <p class="font-bold text-red-300">Incorrecte. Revisa els teus càlculs:</p>
                        <ul class="list-disc list-inside ml-4 mt-2 text-gray-300">
                            <li>Valor Nominal: ${nominalIsCorrect ? '<span class="text-green-300">Correcte</span>' : `<span class="text-red-300">Incorrecte. El valor correcte és ${formatResistance(nominalTarget)}.</span>`}</li>
                            <li>Tolerància: ${toleranceIsCorrect ? '<span class="text-green-300">Correcte</span>' : `<span class="text-red-300">Incorrecte. La tolerància correcta és $\\pm ${toleranceTarget}\\%$.</span>`}</li>
                        </ul>
                    `;
                }

            } else if (currentExercise.type === 'V2C') {
                const b1User = document.getElementById('ex-b1-select').value;
                const b2User = document.getElementById('ex-b2-select').value;
                const b3User = document.getElementById('ex-b3-select').value;
                const b4User = document.getElementById('ex-b4-select').value;
                
                const b1Target = currentExercise.bands[0];
                const b2Target = currentExercise.bands[1];
                const b3Target = currentExercise.bands[2];
                const b4Target = currentExercise.bands[3];
                
                const bandsCorrect = [
                    b1User === b1Target, 
                    b2User === b2Target, 
                    b3User === b3Target, 
                    b4User === b4Target
                ];
                
                // Disable inputs
                document.getElementById('ex-b1-select').disabled = true;
                document.getElementById('ex-b2-select').disabled = true;
                document.getElementById('ex-b3-select').disabled = true;
                document.getElementById('ex-b4-select').disabled = true;
                
                // Show the target bands on the visual
                updateVisualFromBands(document.getElementById('ex-resistor-visual'), currentExercise.bands);


                if (bandsCorrect.every(c => c)) {
                    isCorrect = true;
                    message = `Excel·lent! Has identificat el codi de colors correcte (${b1Target}-${b2Target}-${b3Target}-${b4Target}).`;
                } else {
                    message = `<p class="font-bold text-red-300">Incorrecte. Revisa quines bandes has fallat:</p>
                        <ul class="list-disc list-inside ml-4 mt-2 text-gray-300">
                            <li>Banda 1: ${bandsCorrect[0] ? `<span class="text-green-300">${b1Target} (Correcte)</span>` : `<span class="text-red-300">Incorrecte. Havia de ser ${b1Target}.</span>`}</li>
                            <li>Banda 2: ${bandsCorrect[1] ? `<span class="text-green-300">${b2Target} (Correcte)</span>` : `<span class="text-red-300">Incorrecte. Havia de ser ${b2Target}.</span>`}</li>
                            <li>Banda 3 (Mult.): ${bandsCorrect[2] ? `<span class="text-green-300">${b3Target} (Correcte)</span>` : `<span class="text-red-300">Incorrecte. Havia de ser ${b3Target}.</span>`}</li>
                            <li>Banda 4 (Tol.): ${bandsCorrect[3] ? `<span class="text-green-300">${b4Target} (Correcte)</span>` : `<span class="text-red-300">Incorrecte. Havia de ser ${b4Target}.</span>`}</li>
                        </ul>
                    `;
                }
            }

            feedbackDiv.classList.add('p-4', 'rounded-lg', 'mt-4', isCorrect ? 'bg-green-900' : 'bg-red-900');
            feedbackDiv.innerHTML = message;
            
            document.getElementById('next-exercise-btn').classList.remove('hidden');
            document.getElementById('check-exercise-btn').classList.add('hidden');
            
            if (window.MathJax) window.MathJax.typesetPromise();
        }

        function nextExercise() {
            // Alterna entre C2V i V2C
            currentProblemType = currentProblemType === 'C2V' ? 'V2C' : 'C2V'; 
            generateRandomProblem();
        }

        // --- Funcions de Inicialització i UI de Base ---

        function createSelect(id, bandName, initialColor, isTolerance) {
            const select = document.createElement('select');
            select.id = id;
            select.className = "w-full p-2 border border-gray-600 rounded-lg focus:ring-blue-500 focus:border-blue-500 bg-gray-700-custom text-gray-200 shadow-sm";
            select.onchange = (id.includes('b1') || id.includes('b2') || id.includes('b3') || id.includes('b4')) 
                               ? calculateColorsToValue 
                               : calculateValueToColors;

            if (isTolerance) {
                const toleranceOptions = Object.entries(RESISTOR_COLORS)
                    .filter(([_, data]) => data[COLOR_INDICES.TOLERANCE] !== null)
                    .map(([color, data]) => data[COLOR_INDICES.TOLERANCE]);
                const uniqueTolerances = [...new Set(toleranceOptions)].sort((a, b) => a - b);
                
                uniqueTolerances.forEach(t => {
                    const option = document.createElement('option');
                    option.value = t;
                    option.textContent = `± ${t}%`;
                    select.appendChild(option);
                });
                select.value = 5;
            } else {
                const options = getBandOptions(bandName);
                // Filtre de colors inicials (sense Sense color ni Cap)
                const finalOptions = (bandName === 'band4') 
                    ? options.filter(c => RESISTOR_COLORS[c][COLOR_INDICES.TOLERANCE] !== null) 
                    : options.filter(c => RESISTOR_COLORS[c][COLOR_INDICES.SIGNIFICATIVE] !== null);

                finalOptions.forEach(color => {
                    const option = document.createElement('option');
                    option.value = color;
                    option.textContent = color;
                    option.selected = color === initialColor;
                    option.style.backgroundColor = RESISTOR_COLORS[color][COLOR_INDICES.HEX];
                    option.style.color = (color === "Blanc" || color === "Groc" || color === "Or" || color === "Plata" || color === "Sense color") ? '#000' : '#FFF';
                    select.appendChild(option);
                });
            }

            return select;
        }

        function setupSelectors() {
            // Colors a Valor (C->V)
            document.getElementById('b1-selector-container').appendChild(createSelect('b1-select', 'band1', 'Taronja'));
            document.getElementById('b2-selector-container').appendChild(createSelect('b2-select', 'band2', 'Taronja'));
            document.getElementById('b3-selector-container').appendChild(createSelect('b3-select', 'band3', 'Vermell'));
            document.getElementById('b4-selector-container').appendChild(createSelect('b4-select', 'band4', 'Or'));

            // Valor a Colors (V->C)
            document.getElementById('tolerance-selector-container').appendChild(createSelect('tolerance-select', null, null, true));

            calculateColorsToValue();
            calculateValueToColors();
        }

        // --- MathJax per a les expressions LaTeX ---
        function loadMathJax() {
            const script = document.createElement('script');
            script.type = 'text/javascript';
            script.id = 'MathJax-script';
            script.src = 'https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js';
            script.async = true;
            document.head.appendChild(script);
            
             // Configura MathJax per text clar
            window.MathJax = {
                chtml: {
                    scale: 1, 
                    mtextInheritFont: true,
                    // Estableix un color base clar per a les expressions
                    styles: {
                        '.mjx-chtml': {
                            'color': '#e5e7eb'
                        }
                    }
                },
                tex: {
                    inlineMath: [['$', '$'], ['\\(', '\\)']]
                },
                startup: {
                    pageReady: () => {
                        return MathJax.startup.defaultPageReady().then(() => {
                           if (window.MathJax) window.MathJax.typesetPromise();
                        });
                    }
                }
            };
        }

        function fillTheoryTable() {
            const tbody = document.querySelector('#theory-table tbody');
            const colorKeys = Object.keys(RESISTOR_COLORS).filter(c => c !== "Cap");

            colorKeys.forEach(color => {
                const data = RESISTOR_COLORS[color];
                const hex = data[COLOR_INDICES.HEX];
                
                const textColor = (color === "Blanc" || color === "Groc" || color === "Or" || color === "Plata" || color === "Sense color") ? '#000' : '#FFF';
                const bgColor = color === "Sense color" ? '#8b6b3e' : hex; // Cos del resistor com a fons per a "Sense color"

                const row = document.createElement('tr');
                row.className = 'hover:bg-gray-700 transition duration-100';

                row.innerHTML += `
                    <td class="px-3 py-2 whitespace-nowrap text-sm font-medium text-gray-200 flex items-center">
                        <span class="w-4 h-4 rounded-full mr-2" style="background-color: ${hex}; border: 1px solid #666;"></span>
                        ${color}
                    </td>
                    <td class="px-3 py-2 whitespace-nowrap text-sm text-center font-bold text-gray-200">${data[COLOR_INDICES.SIGNIFICATIVE] !== null ? data[COLOR_INDICES.SIGNIFICATIVE] : '-'}</td>
                    <td class="px-3 py-2 whitespace-nowrap text-sm text-center font-bold text-gray-200">${data[COLOR_INDICES.SIGNIFICATIVE] !== null ? data[COLOR_INDICES.SIGNIFICATIVE] : '-'}</td>
                    <td class="px-3 py-2 whitespace-nowrap text-sm text-center text-gray-200">${data[COLOR_INDICES.MULTIPLIER] !== null ? (data[COLOR_INDICES.MULTIPLIER] >= 1 ? `$\\times 10^{${Math.log10(data[COLOR_INDICES.MULTIPLIER])}}$` : `$\\times ${data[COLOR_INDICES.MULTIPLIER]}$`) : '-'}</td>
                    <td class="px-3 py-2 whitespace-nowrap text-sm text-center font-semibold text-gray-200">${data[COLOR_INDICES.TOLERANCE] !== null ? `$\\pm ${data[COLOR_INDICES.TOLERANCE]}\\%$` : '-'}</td>
                `;
                tbody.appendChild(row);
            });
            if (window.MathJax) window.MathJax.typesetPromise();
        }

        window.onload = function() {
            loadMathJax(); // Carrega MathJax primer
            setupSelectors();
            fillTheoryTable();
            // Inicia la secció d'exercicis
            generateRandomProblem(); 
            document.getElementById('nominal-value-input').addEventListener('input', calculateValueToColors);
        };
    </script>
</head>
<body class="p-4 sm:p-8">

    <div class="max-w-4xl mx-auto text-gray-200">
        <h1 class="text-4xl font-extrabold text-blue-400 mb-8 text-center">Calculadora de Codi de Colors de Resistències</h1>

        <!-- SECCIÓ 1: TEORIA I TAULA -->
        <div class="container-section">
            <h2 class="text-3xl font-bold text-blue-300 mb-6 border-b border-gray-700 pb-2">1. Teoria i Taula de Valors</h2>
            
            <!-- Resistor Visual General -->
            <div class="resistor-visual-container flex items-center w-full max-w-lg mx-auto mb-8 h-12">
                <div class="resistor-lead"></div>
                <div class="resistor-body">
                    <div id="vis-band-1" class="resistor-band band-1"></div>
                    <div id="vis-band-2" class="resistor-band band-2"></div>
                    <div id="vis-band-3" class="resistor-band band-3"></div>
                    <div id="vis-band-4" class="resistor-band band-4"></div>
                </div>
                <div class="resistor-lead"></div>
            </div>

            <p class="mb-4 text-gray-300">Els resistors limiten el pas del corrent elèctric. Utilitzem el codi de 4 bandes per determinar-ne el valor, on les primeres dues bandes són les xifres significatives, la tercera és el multiplicador, i la quarta és la tolerància.</p>

            <h3 class="text-xl font-semibold text-blue-300 mb-3 border-b border-gray-700 pb-1">Taula de Correspondència de Colors</h3>
            <div class="overflow-x-auto rounded-lg shadow-lg">
                <table id="theory-table" class="min-w-full divide-y divide-gray-700">
                    <thead class="bg-blue-600 text-white">
                        <tr>
                            <th class="px-3 py-2 text-left text-xs font-bold uppercase tracking-wider">Color</th>
                            <th class="px-3 py-2 text-left text-xs font-bold uppercase tracking-wider">1a Xifra</th>
                            <th class="px-3 py-2 text-left text-xs font-bold uppercase tracking-wider">2a Xifra</th>
                            <th class="px-3 py-2 text-left text-xs font-bold uppercase tracking-wider">Multiplicador</th>
                            <th class="px-3 py-2 text-left text-xs font-bold uppercase tracking-wider">Tolerància</th>
                        </tr>
                    </thead>
                    <tbody class="bg-gray-900 divide-y divide-gray-700">
                        <!-- S'omple amb JS -->
                    </tbody>
                </table>
            </div>
        </div>

        <!-- SECCIÓ 2: COLORS A VALOR -->
        <div class="container-section">
            <h2 class="text-3xl font-bold text-blue-300 mb-6 border-b border-gray-700 pb-2">2. Calculadora: Colors $\to$ Valor ($\Omega$)</h2>
            <p class="mb-6 text-gray-300">Selecciona els quatre colors del resistor per calcular el seu valor nominal i els seus marges de tolerància.</p>

            <!-- Visualització específica per C->V -->
            <div id="cv-resistor-visual" class="resistor-visual-container flex items-center w-full max-w-sm mx-auto mb-8 h-12">
                <div class="resistor-lead"></div>
                <div class="resistor-body">
                    <div id="vis-band-1" class="resistor-band band-1"></div>
                    <div id="vis-band-2" class="resistor-band band-2"></div>
                    <div id="vis-band-3" class="resistor-band band-3"></div>
                    <div id="vis-band-4" class="resistor-band band-4"></div>
                </div>
                <div class="resistor-lead"></div>
            </div>

            <div class="grid grid-cols-2 sm:grid-cols-4 gap-4 mb-6">
                <div>
                    <label class="block text-sm font-medium text-gray-300 mb-1">Banda 1</label>
                    <div id="b1-selector-container"></div>
                </div>
                <div>
                    <label class="block text-sm font-medium text-gray-300 mb-1">Banda 2</label>
                    <div id="b2-selector-container"></div>
                </div>
                <div>
                    <label class="block text-sm font-medium text-gray-300 mb-1">Banda 3 (Mult.)</label>
                    <div id="b3-selector-container"></div>
                </div>
                <div>
                    <label class="block text-sm font-medium text-gray-300 mb-1">Banda 4 (Tol.)</label>
                    <div id="b4-selector-container"></div>
                </div>
            </div>

            <div id="colors-to-value-result" class="p-4 rounded-xl shadow-lg border-l-4 border-blue-500 bg-gray-700-custom">
                <!-- Resultats aquí -->
            </div>
        </div>

        <!-- SECCIÓ 3: VALOR A COLORS -->
        <div class="container-section">
            <h2 class="text-3xl font-bold text-blue-300 mb-6 border-b border-gray-700 pb-2">3. Calculadora: Valor Nominal $\to$ Colors</h2>
            <p class="mb-6 text-gray-300">Introdueix el valor desitjat i la tolerància per trobar el codi de colors corresponent de 4 bandes.</p>
            
             <!-- Visualització específica per V->C -->
            <div id="vc-resistor-visual" class="resistor-visual-container flex items-center w-full max-w-sm mx-auto mb-8 h-12">
                <div class="resistor-lead"></div>
                <div class="resistor-body">
                    <div id="vis-band-1" class="resistor-band band-1"></div>
                    <div id="vis-band-2" class="resistor-band band-2"></div>
                    <div id="vis-band-3" class="resistor-band band-3"></div>
                    <div id="vis-band-4" class="resistor-band band-4"></div>
                </div>
                <div class="resistor-lead"></div>
            </div>

            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 mb-6">
                <div>
                    <label for="nominal-value-input" class="block text-sm font-medium text-gray-300 mb-1">Valor Nominal ($\Omega$)</label>
                    <input type="number" id="nominal-value-input" value="3300" placeholder="Ex: 3300" min="0" step="any" class="w-full p-2 border border-gray-600 rounded-lg focus:ring-blue-500 focus:border-blue-500 bg-gray-700-custom text-gray-200 shadow-sm">
                </div>
                <div>
                    <label class="block text-sm font-medium text-gray-300 mb-1">Tolerància Desitjada</label>
                    <div id="tolerance-selector-container"></div>
                </div>
            </div>
            
            <button onclick="calculateValueToColors()" class="w-full bg-green-600 hover:bg-green-700 text-white font-bold py-3 px-4 rounded-lg transition duration-150 ease-in-out shadow-lg mb-6">
                Calcular Colors
            </button>

            <div id="value-to-colors-result" class="p-4 rounded-xl shadow-lg border-l-4 border-green-500 bg-gray-700-custom">
                <!-- Resultats aquí -->
            </div>
        </div>
        
        <!-- SECCIÓ 4: EXERCICIS INTERACTIUS -->
        <div class="container-section">
            <h2 class="text-3xl font-bold text-blue-300 mb-6 border-b border-gray-700 pb-2">4. Exercicis Interactius</h2>
            <p class="mb-6 text-gray-300">Posa a prova els teus coneixements. El tipus de problema (Colors a Valor o Valor a Colors) canvia automàticament.</p>
            
            <!-- Visualització específica per Exercicis -->
            <div id="ex-resistor-visual" class="resistor-visual-container flex items-center w-full max-w-sm mx-auto mb-8 h-12">
                <div class="resistor-lead"></div>
                <div class="resistor-body">
                    <div id="vis-band-1" class="resistor-band band-1"></div>
                    <div id="vis-band-2" class="resistor-band band-2"></div>
                    <div id="vis-band-3" class="resistor-band band-3"></div>
                    <div id="vis-band-4" class="resistor-band band-4"></div>
                </div>
                <div class="resistor-lead"></div>
            </div>

            <div id="exercise-problem-display" class="mb-6 p-4 bg-gray-800 rounded-lg border border-gray-600">
                <!-- El problema (colors o valor) es renderitza aquí -->
            </div>

            <div id="exercise-input-fields" class="mb-6">
                <!-- Camps d'entrada/selectors es renderitzen aquí -->
            </div>
            
            <div class="flex flex-col sm:flex-row gap-4">
                <button id="check-exercise-btn" onclick="checkExerciseSolution()" class="flex-1 bg-yellow-600 hover:bg-yellow-700 text-white font-bold py-3 px-4 rounded-lg transition duration-150 ease-in-out shadow-lg">
                    Comprovar
                </button>
                <button id="next-exercise-btn" onclick="nextExercise()" class="hidden flex-1 bg-blue-600 hover:bg-blue-700 text-white font-bold py-3 px-4 rounded-lg transition duration-150 ease-in-out shadow-lg">
                    Següent Exercici (Canvia de tipus)
                </button>
            </div>

            <div id="exercise-feedback" class="p-4 rounded-xl mt-4 text-gray-200 shadow-xl hidden">
                <!-- Feedback es mostra aquí -->
            </div>
        </div>

    </div>
</body>
</html>
