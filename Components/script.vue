<script>
new Vue({
    el: "#app_basic",
    data: {
        
    }
})
Sample film data (you can replace this with your own data) 
import { ref } from 'vue';

const films = [
    { title: "Muhtar ebet tatar", director: "Andrey Panin", year: 2020, link: 'images/sexyImage.png' },
    { title: "School 13", director: "Night Wayfarer", year: 2019, link: 'images/beesechurger' },
    { title: "zreluya sisastaya baba", director: "Jonny Sus", year: 2018, link: 'images/csquad' },
];

const filmList = document.getElementById("film-list");
const filmDetailsContent = document.getElementById("film-details-content");

// Function to display film details
function displayFilmDetails(films) {
    filmDetailsContent.innerHTML = `
        <p><strong>Title:</strong> ${films.title}</p>
        <p><strong>Director:</strong> ${films.director}</p>
        <p><strong>Year:</strong> ${films.year}</p>
    `;
}

// Function to populate the film list
function populateFilmList() {
    films.forEach((film, index) => {
        const listItem = document.createElement("li");
        listItem.textContent = film.title;

        listItem.addEventListener("click", () => {
            displayFilmDetails(films[index]);
        });

        filmList.appendChild(listItem);
    });
}

// Initial population of the film list
populateFilmList();

// Display the details of the first film initially
if (films.length > 0) {
    displayFilmDetails(films[0]);
}
var images = document.getElementById("container")
/*images.style.top = "100px";
images.style.left = "100px";*/

const menu = document.getElementById('menu');
const menuItems = menu.querySelectorAll('li');

let currentIndex = 0;

function scrollToItem(index) {
    if (index < 0) index = 0;
    if (index >= menuItems.length) index = menuItems.length - 1;

    currentIndex = index;

    const item = menuItems[index];
    const itemLeftOffset = item.offsetLeft;
    const containerScrollLeft = menu.scrollLeft;

    menu.scrollTo({
        left: itemLeftOffset - (menu.clientWidth - item.clientWidth) / 2 + containerScrollLeft,
        behavior: 'smooth'
    });
}

menuItems.forEach((item, index) => {
    item.addEventListener('click', () => {
        scrollToItem(index);
    });
});

// Scroll to the first item initially
scrollToItem(0); 
</script>