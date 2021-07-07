# Shota Donguzashvili

#### Phone: +995 598 33 58 85

#### E-mail: shota.nope@gmail.com || [Link to Linkedin](https://www.linkedin.com/in/shota-donguzashvili-457280202) ||[Link to GitHub](https://github.com/donguzashvili)

---

> I'm specializing in front end development and UI/UX desighn,but my goal is to become professional Full Stack Developer.

# `Skills`

> **Progamming Languages**: HTML/CSS/SCSS, JavaScript,TypeScript,C#<br>
> **Frameworks**: ReactJs, Bootstrap,TailWind CSS<br>
> **Module bundler Tool**: WebPack <br>
> **Methodologies**: Object-Poriented Programming, Functional Programming<br>
> **Version control**: GitHub

## `Experience`

### [Link to Portfolio](https://donguzashvili.github.io/myPortfolio/)

## `Education`

- IT Step To Georgia #`Languages`
- **English** | B2
- **Georgian** | Native #`Example of my code`

```Javascript
const searchBtn = document.getElementById('search-btn')
const mealList = document.getElementById('meal')
const mealDetailsContent = document.getElementById('meal-details-content')
const recipeCloseBtn = document.getElementById('recipe-close-btn')

//eventlisteners

searchBtn.addEventListener('click', getMealList)
mealList.addEventListener('click', getMealRecipe)
recipeCloseBtn.addEventListener('click', () => {
    mealDetailsContent.parentElement.classList.remove('showRecipe')
})

//functions
function getMealList(){
    let searchInputTxt = document.getElementById('search-input').value.trim();
    fetch(`https://www.themealdb.com/api/json/v1/1/search.php?s=${searchInputTxt}`)
        .then(res => res.json())
        .then(data => {
            let html = ''
            if(data.meals){
                data.meals.forEach(meal => {
                    html += `<div class="meal-item" data-id="${meal.idMeal}">
                    <div class="meal-img">
                        <img src=${meal.strMealThumb} alt="Food">
                    </div>
                    <div class="meal-name">
                        <h3>"${meal.strMeal}"</h3>
                        <a href="#" class="recipe-btn">Get Recipe</a>
                    </div>
                </div>`
                })
                mealList.classList.remove('notFound')
            }else{
                html = "Sorry, there is no meal like that"
                mealList.classList.add('notFound')
            }
        mealList.innerHTML = html;
        })

}
// get meal recipe
function getMealRecipe(e){
    e.preventDefault()
    if(e.target.classList.contains('recipe-btn')){
        let mealItem = e.target.parentElement.parentElement;
        fetch(`https://www.themealdb.com/api/json/v1/1/lookup.php?i=${mealItem.dataset.id}`)
            .then(response => response.json())
            .then(data => mealRecipeModal(data.meals))
    }
}
// createing modal
function  mealRecipeModal(meal){
    meal = meal[0]
    mealDetailsContent.innerHTML = `
                <h2 class="recipe-title">${meal.strMeal}</h2>
                    <p class="recipe-category">${meal.strCategory}</p>
                    <div class="recipe-instruction">Instructions:</div>
                    <p>${meal.strInstructions}</p>
                </div>
                <div class="recipe-meal-img">
                    <img src="${meal.strMealThumb}" alt="food">
                </div>
                <div class="recipe-link">
                    <a href="${meal.strYoutube}" target="_blank">Watch video</a>
                </div>
    `;
    mealDetailsContent.parentElement.classList.add("showRecipe")

}
```
