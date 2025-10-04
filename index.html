<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Meal Planner</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/react/18.2.0/umd/react.production.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/react-dom/18.2.0/umd/react-dom.production.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-standalone/7.23.5/babel.min.js"></script>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        body {
            margin: 0;
            padding: 0;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen', 'Ubuntu', 'Cantarell', sans-serif;
        }
    </style>
</head>
<body>
    <div id="root"></div>

    <script type="text/babel">
        const { useState, useEffect } = React;

        // Storage helper functions using IndexedDB
        const DB_NAME = 'MealPlannerDB';
        const DB_VERSION = 1;
        const STORE_NAME = 'meals';

        const initDB = () => {
            return new Promise((resolve, reject) => {
                const request = indexedDB.open(DB_NAME, DB_VERSION);
                
                request.onerror = () => reject(request.error);
                request.onsuccess = () => resolve(request.result);
                
                request.onupgradeneeded = (event) => {
                    const db = event.target.result;
                    if (!db.objectStoreNames.contains(STORE_NAME)) {
                        db.createObjectStore(STORE_NAME);
                    }
                };
            });
        };

        const saveData = async (key, data) => {
            try {
                const db = await initDB();
                const transaction = db.transaction([STORE_NAME], 'readwrite');
                const store = transaction.objectStore(STORE_NAME);
                store.put(data, key);
                return new Promise((resolve, reject) => {
                    transaction.oncomplete = () => resolve();
                    transaction.onerror = () => reject(transaction.error);
                });
            } catch (error) {
                console.error('Error saving data:', error);
            }
        };

        const loadData = async (key) => {
            try {
                const db = await initDB();
                const transaction = db.transaction([STORE_NAME], 'readonly');
                const store = transaction.objectStore(STORE_NAME);
                const request = store.get(key);
                return new Promise((resolve, reject) => {
                    request.onsuccess = () => resolve(request.result);
                    request.onerror = () => reject(request.error);
                });
            } catch (error) {
                console.error('Error loading data:', error);
                return null;
            }
        };

        // Lucide icons as inline SVG components
        const Plus = ({ className }) => (
            <svg className={className} fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M12 4v16m8-8H4" />
            </svg>
        );

        const Trash2 = ({ className }) => (
            <svg className={className} fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16" />
            </svg>
        );

        const ShoppingCart = ({ className }) => (
            <svg className={className} fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z" />
            </svg>
        );

        const ChefHat = ({ className }) => (
            <svg className={className} fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M12 2C8.134 2 5 5.134 5 9v3H3v8h18v-8h-2V9c0-3.866-3.134-7-7-7z" />
                <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M8 20h8" />
            </svg>
        );

        const Download = ({ className }) => (
            <svg className={className} fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M21 15v4a2 2 0 01-2 2H5a2 2 0 01-2-2v-4m4-5l5 5 5-5m-5 5V3" />
            </svg>
        );

        const Upload = ({ className }) => (
            <svg className={className} fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M21 15v4a2 2 0 01-2 2H5a2 2 0 01-2-2v-4m14-7l-5-5-5 5m5-5v12" />
            </svg>
        );

        function MealPlanner() {
            const [meals, setMeals] = useState([]);
            const [selectedMeals, setSelectedMeals] = useState([]);
            const [newMealName, setNewMealName] = useState('');
            const [newIngredient, setNewIngredient] = useState('');
            const [editingMeal, setEditingMeal] = useState(null);
            const [showShoppingList, setShowShoppingList] = useState(false);
            const [isLoading, setIsLoading] = useState(true);

            // Load data on mount
            useEffect(() => {
                const loadSavedData = async () => {
                    const savedMeals = await loadData('meals');
                    const savedSelected = await loadData('selectedMeals');
                    
                    if (savedMeals) setMeals(savedMeals);
                    if (savedSelected) setSelectedMeals(savedSelected);
                    setIsLoading(false);
                };
                
                loadSavedData();
            }, []);

            // Save meals whenever they change
            useEffect(() => {
                if (!isLoading) {
                    saveData('meals', meals);
                }
            }, [meals, isLoading]);

            // Save selected meals whenever they change
            useEffect(() => {
                if (!isLoading) {
                    saveData('selectedMeals', selectedMeals);
                }
            }, [selectedMeals, isLoading]);

            const addMeal = () => {
                if (newMealName.trim()) {
                    setMeals([...meals, { id: Date.now(), name: newMealName, ingredients: [] }]);
                    setNewMealName('');
                }
            };

            const deleteMeal = (id) => {
                setMeals(meals.filter(m => m.id !== id));
                setSelectedMeals(selectedMeals.filter(mId => mId !== id));
            };

            const addIngredient = (mealId) => {
                if (newIngredient.trim()) {
                    setMeals(meals.map(m => 
                        m.id === mealId 
                            ? { ...m, ingredients: [...m.ingredients, newIngredient] }
                            : m
                    ));
                    setNewIngredient('');
                }
            };

            const removeIngredient = (mealId, ingredientIndex) => {
                setMeals(meals.map(m =>
                    m.id === mealId
                        ? { ...m, ingredients: m.ingredients.filter((_, i) => i !== ingredientIndex) }
                        : m
                ));
            };

            const toggleMealSelection = (mealId) => {
                setSelectedMeals(prev =>
                    prev.includes(mealId)
                        ? prev.filter(id => id !== mealId)
                        : [...prev, mealId]
                );
            };

            const generateShoppingList = () => {
                const ingredientCounts = {};
                
                selectedMeals.forEach(mealId => {
                    const meal = meals.find(m => m.id === mealId);
                    meal?.ingredients.forEach(ing => {
                        const lowerIng = ing.toLowerCase();
                        ingredientCounts[lowerIng] = (ingredientCounts[lowerIng] || 0) + 1;
                    });
                });

                return Object.entries(ingredientCounts).map(([ing, count]) => ({
                    ingredient: ing,
                    count
                }));
            };

            const exportData = () => {
                const data = {
                    meals,
                    selectedMeals,
                    exportDate: new Date().toISOString()
                };
                const blob = new Blob([JSON.stringify(data, null, 2)], { type: 'application/json' });
                const url = URL.createObjectURL(blob);
                const a = document.createElement('a');
                a.href = url;
                a.download = 'meal-planner-backup.json';
                a.click();
                URL.revokeObjectURL(url);
            };

            const importData = (event) => {
                const file = event.target.files[0];
                if (file) {
                    const reader = new FileReader();
                    reader.onload = (e) => {
                        try {
                            const data = JSON.parse(e.target.result);
                            if (data.meals) setMeals(data.meals);
                            if (data.selectedMeals) setSelectedMeals(data.selectedMeals);
                            alert('Data imported successfully!');
                        } catch (error) {
                            alert('Error importing data. Please check the file format.');
                        }
                    };
                    reader.readAsText(file);
                }
            };

            const shoppingList = generateShoppingList();

            if (isLoading) {
                return (
                    <div className="min-h-screen bg-gradient-to-br from-orange-50 to-amber-50 flex items-center justify-center">
                        <div className="text-center">
                            <ChefHat className="w-16 h-16 mx-auto mb-4 text-orange-600 animate-pulse" />
                            <p className="text-gray-600">Loading your meals...</p>
                        </div>
                    </div>
                );
            }

            return (
                <div className="min-h-screen bg-gradient-to-br from-orange-50 to-amber-50 p-6">
                    <div className="max-w-6xl mx-auto">
                        <div className="bg-white rounded-2xl shadow-xl p-8 mb-6">
                            <div className="flex items-center justify-between mb-6">
                                <div className="flex items-center gap-3">
                                    <ChefHat className="w-8 h-8 text-orange-600" />
                                    <h1 className="text-3xl font-bold text-gray-800">Meal Planner</h1>
                                </div>
                                <div className="flex gap-2">
                                    <button
                                        onClick={exportData}
                                        className="bg-gray-100 text-gray-700 px-4 py-2 rounded-lg hover:bg-gray-200 flex items-center gap-2 transition text-sm"
                                        title="Export backup"
                                    >
                                        <Download className="w-4 h-4" />
                                        <span className="hidden sm:inline">Backup</span>
                                    </button>
                                    <label className="bg-gray-100 text-gray-700 px-4 py-2 rounded-lg hover:bg-gray-200 flex items-center gap-2 transition cursor-pointer text-sm">
                                        <Upload className="w-4 h-4" />
                                        <span className="hidden sm:inline">Restore</span>
                                        <input
                                            type="file"
                                            accept=".json"
                                            onChange={importData}
                                            className="hidden"
                                        />
                                    </label>
                                </div>
                            </div>

                            {/* Add New Meal */}
                            <div className="flex gap-2 mb-8">
                                <input
                                    type="text"
                                    value={newMealName}
                                    onChange={(e) => setNewMealName(e.target.value)}
                                    onKeyPress={(e) => e.key === 'Enter' && addMeal()}
                                    placeholder="Enter meal name..."
                                    className="flex-1 px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-orange-500"
                                />
                                <button
                                    onClick={addMeal}
                                    className="bg-orange-600 text-white px-6 py-2 rounded-lg hover:bg-orange-700 flex items-center gap-2 transition"
                                >
                                    <Plus className="w-5 h-5" />
                                    <span className="hidden sm:inline">Add Meal</span>
                                </button>
                            </div>

                            {/* Meals List */}
                            <div className="grid md:grid-cols-2 gap-4 mb-6">
                                {meals.map(meal => (
                                    <div key={meal.id} className="border border-gray-200 rounded-lg p-4 bg-gray-50">
                                        <div className="flex items-start justify-between mb-3">
                                            <div className="flex items-center gap-2 flex-1">
                                                <input
                                                    type="checkbox"
                                                    checked={selectedMeals.includes(meal.id)}
                                                    onChange={() => toggleMealSelection(meal.id)}
                                                    className="w-5 h-5 text-orange-600 rounded focus:ring-orange-500"
                                                />
                                                <h3 className="font-semibold text-lg text-gray-800">{meal.name}</h3>
                                            </div>
                                            <button
                                                onClick={() => deleteMeal(meal.id)}
                                                className="text-red-500 hover:text-red-700 transition"
                                            >
                                                <Trash2 className="w-5 h-5" />
                                            </button>
                                        </div>

                                        {/* Ingredients */}
                                        <div className="mb-2">
                                            {meal.ingredients.map((ing, idx) => (
                                                <div key={idx} className="flex items-center justify-between py-1 px-2 bg-white rounded mb-1">
                                                    <span className="text-gray-700">{ing}</span>
                                                    <button
                                                        onClick={() => removeIngredient(meal.id, idx)}
                                                        className="text-gray-400 hover:text-red-500 text-sm"
                                                    >
                                                        ×
                                                    </button>
                                                </div>
                                            ))}
                                        </div>

                                        {/* Add Ingredient */}
                                        <div className="flex gap-2 mt-2">
                                            <input
                                                type="text"
                                                value={editingMeal === meal.id ? newIngredient : ''}
                                                onChange={(e) => setNewIngredient(e.target.value)}
                                                onFocus={() => setEditingMeal(meal.id)}
                                                onKeyPress={(e) => {
                                                    if (e.key === 'Enter') {
                                                        addIngredient(meal.id);
                                                        setEditingMeal(null);
                                                    }
                                                }}
                                                placeholder="Add ingredient..."
                                                className="flex-1 px-3 py-1 text-sm border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-orange-500"
                                            />
                                            <button
                                                onClick={() => {
                                                    addIngredient(meal.id);
                                                    setEditingMeal(null);
                                                }}
                                                className="bg-orange-100 text-orange-600 px-3 py-1 rounded text-sm hover:bg-orange-200 transition"
                                            >
                                                <Plus className="w-4 h-4" />
                                            </button>
                                        </div>
                                    </div>
                                ))}
                            </div>

                            {meals.length === 0 && (
                                <div className="text-center py-12 text-gray-400">
                                    <ChefHat className="w-16 h-16 mx-auto mb-3 opacity-50" />
                                    <p>No meals yet. Add your first meal above!</p>
                                </div>
                            )}
                        </div>

                        {/* Shopping List */}
                        {selectedMeals.length > 0 && (
                            <div className="bg-white rounded-2xl shadow-xl p-8">
                                <button
                                    onClick={() => setShowShoppingList(!showShoppingList)}
                                    className="flex items-center gap-3 mb-4 text-xl font-bold text-gray-800 w-full"
                                >
                                    <ShoppingCart className="w-6 h-6 text-orange-600" />
                                    Shopping List ({shoppingList.length} items)
                                </button>
                                
                                {showShoppingList && (
                                    <div className="space-y-2">
                                        {shoppingList.map((item, idx) => (
                                            <div key={idx} className="flex items-center justify-between py-2 px-4 bg-orange-50 rounded-lg">
                                                <span className="text-gray-800 capitalize">{item.ingredient}</span>
                                                {item.count > 1 && (
                                                    <span className="bg-orange-600 text-white px-3 py-1 rounded-full text-sm">
                                                        × {item.count}
                                                    </span>
                                                )}
                                            </div>
                                        ))}
                                    </div>
                                )}
                            </div>
                        )}
                    </div>
                </div>
            );
        }

        ReactDOM.render(<MealPlanner />, document.getElementById('root'));
    </script>
</body>
</html>
