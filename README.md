<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Promotional Item Submission</title>
    <!-- Use Inter font from Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        body {
            font-family: 'Inter', sans-serif;
        }
        /* Custom scrollbar for better aesthetics */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-thumb {
            background: #9ca3af;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #6b7280;
        }
        @media print {
            body {
                background-color: #fff !important;
                color: #000 !important;
                padding: 0 !important;
            }
            .no-print {
                display: none !important;
            }
            .print-area {
                width: 100% !important;
                max-width: none !important;
                box-shadow: none !important;
                padding: 0 !important;
                margin: 0 !important;
            }
            header, form, .bg-gray-50, .bg-blue-50, .border-gray-200, .border-blue-200 {
                box-shadow: none !important;
                background-color: transparent !important;
            }
            /* Style for a more report-like appearance */
            .item-card-print {
                flex-direction: row;
                align-items: center;
                border: 1px solid #e5e7eb;
                margin-bottom: 1rem;
                padding: 1rem;
            }
            .item-card-print img {
                width: 6rem;
                height: 6rem;
                margin-right: 1.5rem;
                margin-bottom: 0;
            }
        }
    </style>
</head>
<body class="bg-gray-100 text-gray-800 p-4 sm:p-6 md:p-8">
    <div class="max-w-4xl mx-auto bg-white rounded-2xl shadow-xl p-6 sm:p-8 md:p-10 print-area">
        <!-- Header Section -->
        <header class="text-center mb-8">
            <h1 class="text-3xl sm:text-4xl font-bold text-gray-900 mb-2">Promotional Item Submission</h1>
            <p class="text-gray-600 no-print">Please fill out the form below to submit your item details.</p>
        </header>

        <!-- Main Content Grid -->
        <main class="grid lg:grid-cols-2 gap-8">
            <!-- Submission Form (hidden in print) -->
            <div class="bg-gray-50 p-6 rounded-xl border border-gray-200 h-fit no-print">
                <!-- Team Selection Section -->
                <div class="mb-6 space-y-4">
                    <h2 class="text-2xl font-semibold text-gray-800 mb-2">Select Your Team</h2>
                    <div class="flex items-center space-x-2">
                        <!-- Dropdown Menu for Teams -->
                        <select id="teamSelect" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 transition-colors duration-200">
                            <option value="">Select a Team...</option>
                            <option value="Arcadia">Arcadia</option>
                            <option value="Rush">Rush</option>
                            <option value="Yards at Old State">Yards at Old State</option>
                            <option value="Atmosphere">Atmosphere</option>
                            <option value="Aspen Tampa">Aspen Tampa</option>
                            <option value="NxNW">NxNW</option>
                            <option value="Quarry Trail">Quarry Trail</option>
                            <option value="The Cottages at Lake Tamaha">The Cottages at Lake Tamaha</option>
                            <option value="Midtown Stillwater">Midtown Stillwater</option>
                            <option value="Millennium Norman">Millennium Norman</option>
                            <option value="Montara Park">Montara Park</option>
                            <option value="The Flats at Norman">The Flats at Norman</option>
                        </select>
                    </div>
                    <p id="currentTeamDisplay" class="text-sm font-medium text-gray-700">No team loaded.</p>
                </div>
                
                <h2 class="text-2xl font-semibold text-gray-800 mb-4">Add a New Item</h2>
                <form id="submissionForm" class="space-y-4">
                    <!-- Item Image File Input -->
                    <div>
                        <label for="itemImageFile" class="block text-sm font-medium text-gray-700 mb-1">Upload Item Image</label>
                        <input type="file" id="itemImageFile" name="itemImageFile" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 transition-colors duration-200" accept="image/*" required>
                    </div>
                    <!-- Item Link Input -->
                    <div>
                        <label for="itemLink" class="block text-sm font-medium text-gray-700 mb-1">Item Link</label>
                        <input type="url" id="itemLink" name="itemLink" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 transition-colors duration-200" placeholder="https://example.com/product-page" required>
                    </div>
                    <!-- Item Cost Input -->
                    <div>
                        <label for="itemCost" class="block text-sm font-medium text-gray-700 mb-1">Cost per Item ($)</label>
                        <input type="number" id="itemCost" name="itemCost" min="0" step="0.01" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 transition-colors duration-200" placeholder="e.g., 5.99" required>
                    </div>
                    <!-- Quantity Input -->
                    <div>
                        <label for="itemQuantity" class="block text-sm font-medium text-gray-700 mb-1">Quantity</label>
                        <input type="number" id="itemQuantity" name="itemQuantity" min="1" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 transition-colors duration-200" placeholder="e.g., 100" required>
                    </div>
                    <!-- Submit Button -->
                    <button type="submit" id="submitButton" class="w-full bg-blue-600 text-white font-semibold py-3 px-4 rounded-lg shadow-md hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 transition-colors duration-200" disabled>
                        Add Item
                    </button>
                    <!-- Message Box for Alerts -->
                    <div id="message-box" class="p-3 bg-red-100 text-red-700 rounded-lg text-sm hidden"></div>
                </form>
            </div>

            <!-- Item List and Budget Summary -->
            <div>
                <!-- Budget Summary -->
                <div class="bg-blue-50 p-6 rounded-xl border border-blue-200 mb-6">
                    <h2 class="text-2xl font-semibold text-blue-800 mb-2">Total Budget</h2>
                    <p class="text-4xl font-bold text-blue-600" id="totalBudgetDisplay">$0.00</p>
                    <!-- New Print Button -->
                    <button id="printButton" class="w-full bg-blue-600 text-white font-semibold py-3 px-4 rounded-lg shadow-md hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 transition-colors duration-200 mt-4 no-print">
                        Print Report
                    </button>
                </div>
                
                <!-- Submitted Items List -->
                <div class="bg-gray-50 p-6 rounded-xl border border-gray-200">
                    <h2 class="text-2xl font-semibold text-gray-800 mb-4">Submitted Items</h2>
                    <div id="itemList" class="space-y-4">
                        <!-- Items will be dynamically added here -->
                        <p class="text-gray-500 text-center" id="noItemsMessage">Select a team to get started.</p>
                    </div>
                </div>
            </div>
        </main>
    </div>

    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, doc, getDoc, addDoc, setDoc, updateDoc, deleteDoc, onSnapshot, collection, query, where } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";
        import { getStorage, ref, uploadBytes, getDownloadURL } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-storage.js";

        // Global variables for Firebase
        const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';
        const firebaseConfig = JSON.parse(typeof __firebase_config !== 'undefined' ? __firebase_config : '{}');
        const initialAuthToken = typeof __initial_auth_token !== 'undefined' ? __initial_auth_token : null;

        let db, auth, storage;
        let unsubscribe = null; // To store the onSnapshot listener

        // Get references to DOM elements
        const form = document.getElementById('submissionForm');
        const itemList = document.getElementById('itemList');
        const totalBudgetDisplay = document.getElementById('totalBudgetDisplay');
        const noItemsMessage = document.getElementById('noItemsMessage');
        const messageBox = document.getElementById('message-box');
        const printButton = document.getElementById('printButton');
        const teamSelect = document.getElementById('teamSelect');
        const currentTeamDisplay = document.getElementById('currentTeamDisplay');
        const submitButton = document.getElementById('submitButton');
        const itemImageFile = document.getElementById('itemImageFile');

        let currentTeamId = null;

        /**
         * Initializes Firebase and handles authentication.
         */
        async function initializeFirebase() {
            try {
                const app = initializeApp(firebaseConfig);
                db = getFirestore(app);
                auth = getAuth(app);
                storage = getStorage(app);
                
                // Sign in with custom token if available, otherwise anonymously
                if (initialAuthToken) {
                    await signInWithCustomToken(auth, initialAuthToken);
                } else {
                    await signInAnonymously(auth);
                }
                
                // Initial setup on page load
                onAuthStateChanged(auth, (user) => {
                    if (user) {
                        // User is signed in, Firebase is ready
                        // The UI is ready for team selection
                    } else {
                        // User is signed out, handle as needed
                    }
                });

                console.log("Firebase initialized and authenticated.");
                
            } catch (error) {
                console.error("Error initializing Firebase:", error);
                showMessageBox('Failed to connect to the database. Please try again later.');
            }
        }

        /**
         * Hides the message box.
         */
        function hideMessageBox() {
            messageBox.classList.add('hidden');
            messageBox.textContent = '';
        }

        /**
         * Shows a message in the message box.
         * @param {string} message - The message to display.
         * @param {string} type - The type of message (e.g., 'error', 'success').
         */
        function showMessageBox(message, type = 'error') {
            messageBox.textContent = message;
            messageBox.classList.remove('hidden');
            if (type === 'error') {
                messageBox.classList.remove('bg-green-100', 'text-green-700');
                messageBox.classList.add('bg-red-100', 'text-red-700');
            } else if (type === 'success') {
                messageBox.classList.remove('bg-red-100', 'text-red-700');
                messageBox.classList.add('bg-green-100', 'text-green-700');
            }
        }

        /**
         * Renders the list of items to the DOM.
         * @param {Array} items - The array of items to render.
         */
        function renderItems(items) {
            // Clear the list before re-rendering
            itemList.innerHTML = '';
            
            if (items.length === 0) {
                noItemsMessage.classList.remove('hidden');
                itemList.appendChild(noItemsMessage);
            } else {
                noItemsMessage.classList.add('hidden');
                // Iterate over each item and create a new card element
                items.forEach(item => {
                    const itemCard = document.createElement('div');
                    itemCard.className = 'flex flex-col sm:flex-row items-center bg-white p-4 rounded-xl shadow-sm border border-gray-200 item-card-print';
                    itemCard.innerHTML = `
                        <!-- Item Image -->
                        <img src="${item.image}" alt="Item Image" class="w-24 h-24 object-cover rounded-lg mb-4 sm:mb-0 sm:mr-6 shrink-0" onerror="this.src='https://placehold.co/96x96/e5e7eb/4b5563?text=No+Image'; this.alt='Image not available';">
                        
                        <!-- Item Details -->
                        <div class="flex-grow text-center sm:text-left space-y-1">
                            <p class="text-gray-900 font-semibold text-lg">Total Cost: <span class="text-blue-600">$${item.total.toFixed(2)}</span></p>
                            <p class="text-sm text-gray-600">Cost: $${item.cost.toFixed(2)} | Qty: ${item.quantity}</p>
                            <a href="${item.link}" target="_blank" rel="noopener noreferrer" class="text-blue-500 hover:text-blue-700 text-sm font-medium break-all underline transition-colors duration-200 no-print">
                                View Item Link
                            </a>
                            <span class="no-print text-sm text-gray-500">
                              (Link: ${item.link})
                            </span>
                        </div>
                    `;
                    itemList.appendChild(itemCard);
                });
            }
        }

        /**
         * Calculates and updates the total budget display.
         * @param {Array} items - The array of items to calculate the total for.
         */
        function updateBudget(items) {
            const totalBudget = items.reduce((sum, item) => sum + item.total, 0);
            totalBudgetDisplay.textContent = `$${totalBudget.toFixed(2)}`;
        }

        /**
         * Loads and listens for real-time updates for a specific team's data.
         * @param {string} teamId - The ID of the team to load.
         */
        function loadTeamData(teamId) {
            // Unsubscribe from any previous listener
            if (unsubscribe) {
                unsubscribe();
            }

            const teamPromotionsRef = collection(db, `artifacts/${appId}/public/data/promotions`);
            const q = query(teamPromotionsRef, where("teamId", "==", teamId));

            // Set up a real-time listener
            unsubscribe = onSnapshot(q, (querySnapshot) => {
                const fetchedItems = [];
                querySnapshot.forEach((doc) => {
                    const data = doc.data();
                    fetchedItems.push(data);
                });

                // Render the fetched items and update the budget
                renderItems(fetchedItems);
                updateBudget(fetchedItems);
            }, (error) => {
                console.error("Error getting documents: ", error);
                showMessageBox("Failed to load team data. Please check your team name and connection.");
            });
        }

        // Event listener for the new Print Report button
        printButton.addEventListener('click', () => {
            window.print();
        });

        // Event listener for the new team dropdown
        teamSelect.addEventListener('change', () => {
            const selectedTeam = teamSelect.value;
            if (selectedTeam) {
                currentTeamId = selectedTeam;
                currentTeamDisplay.textContent = `Viewing submissions for: ${selectedTeam}`;
                submitButton.disabled = false;
                noItemsMessage.textContent = 'No items submitted yet for this team.';
                loadTeamData(currentTeamId);
            } else {
                // If a team is deselected, reset the UI
                currentTeamId = null;
                currentTeamDisplay.textContent = `No team loaded.`;
                submitButton.disabled = true;
                noItemsMessage.textContent = 'Select a team to get started.';
                itemList.innerHTML = '';
                totalBudgetDisplay.textContent = '$0.00';
            }
        });
        
        // Handle form submission to add a new item to Firestore
        form.addEventListener('submit', async (event) => {
            event.preventDefault();

            if (!currentTeamId) {
                showMessageBox('Please select a team from the dropdown first.');
                return;
            }

            hideMessageBox();

            const itemLink = document.getElementById('itemLink').value.trim();
            const itemCost = parseFloat(document.getElementById('itemCost').value);
            const itemQuantity = parseInt(document.getElementById('itemQuantity').value);
            const imageFile = itemImageFile.files[0];

            if (!imageFile || !itemLink || isNaN(itemCost) || isNaN(itemQuantity) || itemCost < 0 || itemQuantity < 1) {
                showMessageBox('Please fill out all fields and upload an image.');
                return;
            }

            submitButton.disabled = true;
            showMessageBox('Uploading image, please wait...', 'success');

            try {
                // Create a unique file name
                const fileName = `${currentTeamId}_${Date.now()}_${imageFile.name}`;
                const storageRef = ref(storage, `artifacts/${appId}/public/data/images/${fileName}`);

                // Upload the file
                const snapshot = await uploadBytes(storageRef, imageFile);
                const imageUrl = await getDownloadURL(snapshot.ref);

                // Create the new item object with the image URL
                const newItem = {
                    teamId: currentTeamId,
                    image: imageUrl,
                    link: itemLink,
                    cost: itemCost,
                    quantity: itemQuantity,
                    total: itemCost * itemQuantity,
                    timestamp: Date.now()
                };

                // Add the new item to Firestore
                const teamPromotionsRef = collection(db, `artifacts/${appId}/public/data/promotions`);
                await addDoc(teamPromotionsRef, newItem);

                showMessageBox('Item submitted successfully!', 'success');
                form.reset();
            } catch (e) {
                console.error("Error submitting item: ", e);
                showMessageBox("Error submitting item. Please try again.");
            } finally {
                submitButton.disabled = false;
            }
        });

        initializeFirebase();
    </script>
</body>
</html>
