<div style="text-align: center; margin: 20px 0;">
  <input type="text" id="searchBox" placeholder="Search recipes..." style="padding: 10px; width: 300px; font-size: 16px; border: 2px solid #ddd; border-radius: 5px;">
  <button onclick="clearSearch()" style="padding: 10px 20px; margin-left: 10px; background: #666; color: white; border: none; border-radius: 5px; cursor: pointer;">Clear</button>
</div>

<div id="recipeContent">

---

## 🍖 Mains
<div class="recipe-section">
<div class="recipe-item">

**[Southern Mac N Cheese](mains/southern-mac-n-cheese.md)**  
*"Cheese all through the bitch"*
</div>
<div class="recipe-item">

**[Gila River Bowl of Red](mains/gila-river-bowl-of-red.md)**  
*"These mountains won't be blue, we're going for a banquet"*
</div>
<div class="recipe-item">

**[Pulled Pork](mains/pulled-pork.md)**  
*"on a sandwich, or on its own"*
</div>
<div class="recipe-item">

**[Biscuits and Gravy](mains/biscuits-and-gravy.md)**  
*"Stick to your ribs"*
</div>
<div class="recipe-item">

**[Every Day Pizza Dough](mains/pizza-dough.md)**  
*"Mess one thing up and you're fucked"*
</div>
<div class="recipe-item">

**[Vodka Pasta](mains/vodka-pasta.md)**  
*"Can you get drunk off this?"*
</div>
<div class="recipe-item">

**[Chicken Parmesan](mains/chicken-parmesan.md)**  
*"Dirty every bowl and pan in your kitchen, and make a huge mess cause you're a dirty disgusting person who loves chicken parm"*
</div>
</div>

---

## 🥘 Sides
<div class="recipe-section">
<div class="recipe-item">

**[Cornbread](sides/cornbread.md)**  
*"Not crumbly and crappy"*
</div>
<div class="recipe-item">

**[Collard Greens](sides/collard-greens.md)**  
*"Please for the love of god season them appropriately"*
</div>
<div class="recipe-item">

**[Crispy Butter Biscuits](sides/crispy-butter-biscuits.md)**  
*"Perfect to soak up all that graavy"*
</div>
<div class="recipe-item">

**[All Good Things Chip Dip](sides/all-good-things-chip-dip.md)**  
*"What if we just added everything into a bowl?"*
</div>
</div>

---

## 🧂 Sauces & Rubs
<div class="recipe-section">
<div class="recipe-item">

**[Vinegar Finishing Sauce](sauces-rubs/vinegar-finishing-sauce.md)**  
*"I've never been to North Carolina, but this sauce has"*
</div>
<div class="recipe-item">

**[Pork Rub](sauces-rubs/pork-rub.md)**  
*"Rub me up"*
</div>
<div class="recipe-item">

**[Pizza Sauce](sauces-rubs/pizza-sauce.md)**  
*"Italian accents mandatory"*
</div>
<div class="recipe-item">

**[Every Day Tomato Sauce](sauces-rubs/every-day-tomato-sauce.md)**  
*"Your base for every italian recipe needing a tomato sauce"*
</div>
</div>

---

## 🍰 Desserts
<div class="recipe-section">
<div class="recipe-item">

**[Lemon Bars](desserts/lemon-bars.md)**  
*"I've got nothing to say, lemon bars are amazing"*
</div>
<div class="recipe-item">

**[Crème Brûlée](desserts/creme-brulee.md)**  
*"Everyone gets stoked when the hand torch comes out"*
</div>
<div class="recipe-item">

**[Brown Butter Cake](desserts/brown-butter-cake.md)**  
*"A lazy man's sticky toffee pudding"*
</div>
</div>

---

## 🇦🇲 Armenian
<div class="recipe-section">
<div class="recipe-item">

**[Chodag](armenian/chodag.md)**  
*"It's braided bread"*
</div>
</div>

</div>

---

## 📂 Resources
**[The Wise One BGE Guide](resources/WiseOneRecipes.pdf)** - Essential for overnight smoking

---

*[Back to Top](#ryans-cookbook-)*

<script>
function searchRecipes() {
  var input = document.getElementById('searchBox');
  var filter = input.value.toUpperCase();
  var recipes = document.getElementsByClassName('recipe-item');
  var sections = document.getElementsByTagName('h2');
  var hasResults = false;
  
  // Show/hide recipes
  for (var i = 0; i < recipes.length; i++) {
    var recipe = recipes[i];
    var text = recipe.textContent || recipe.innerText;
    if (text.toUpperCase().indexOf(filter) > -1) {
      recipe.style.display = "";
      hasResults = true;
    } else {
      recipe.style.display = "none";
    }
  }
  
  // Show/hide section headers if they have no visible recipes
  var recipeSections = document.getElementsByClassName('recipe-section');
  for (var i = 0; i < recipeSections.length; i++) {
    var section = recipeSections[i];
    var visibleRecipes = 0;
    var items = section.getElementsByClassName('recipe-item');
    for (var j = 0; j < items.length; j++) {
      if (items[j].style.display !== "none") {
        visibleRecipes++;
      }
    }
    
    // Find the header before this section
    var header = section.previousElementSibling;
    while (header && header.tagName !== 'H2') {
      header = header.previousElementSibling;
    }
    if (header) {
      header.style.display = visibleRecipes > 0 ? "" : "none";
    }
    
    // Hide the HR before the header too
    var hr = header ? header.previousElementSibling : null;
    if (hr && hr.tagName === 'HR') {
      hr.style.display = visibleRecipes > 0 ? "" : "none";
    }
  }
}

function clearSearch() {
  document.getElementById('searchBox').value = '';
  searchRecipes();
}

// Add event listener when page loads
document.addEventListener('DOMContentLoaded', function() {
  var searchBox = document.getElementById('searchBox');
  if (searchBox) {
    searchBox.addEventListener('keyup', searchRecipes);
  }
});
</script>
