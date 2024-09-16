<script >
import { ref } from 'vue'

export default {
    setup() {
        const icons = ref([1,2,3,4,5])
        const selectedIcon = ref(null)
        const showRating = ref(false)

        toggleicons = (index) => {
            const iconIndex = selectedIcon.value.indexOf(index)
            if (iconIndex === -1) {
                selectedIcon.value.push(index)
            } else {
                selectedIcon.value.splice(iconIndex, 1)
            }
        };
         //method to sumbit the rating
         const submitRating = () => {
            showRating.value = true
         }

         //method to close the rating
            const closeRating = () => {
                showRating.value = false
            }

            return {
                icons,
                selectedIcon,
                showRating,
                toggleicons,
                submitRating,
                closeRating
            }

    }
}


</script>

<template>
    <div class="app">
        <div class="icon">
            <img src="/src/assets/images/icon-star.svg" alt="">
        </div>
        <div class="card-text">
            <h1>How did we do?</h1>
            <p>Please let us know how we did with your support request. All feedback is appreciated to help us improve our offering!</p>
        </div>
        <div class="btns">
            <button class="btns-round" v-for="rating in icons" :key="rating" @click="toggleicons(rating)">
                {{ rating }}
            </button>
        </div>
        <div class="btns-submit">
            <button @click="submitRating">SUBMIT</button>
        </div>
    </div>

    <div v-if="showRating" class="rating-modal">
        <div class="rating-modal-content">
            <h2>Thank you for your rating!</h2>
            <p>We appreciate your feedback.</p>
            <button @click="closeRating">Close</button>
        </div>
    </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Overpass:ital,wght@0,100..900;1,100..900&display=swap');

.app {
    width: 350px;
    height: 500px;
    display: flex;
    flex-direction: column;
    align-items: start;
    justify-content: space-between;
    font-family: "Overpass", sans-serif;
    background-color: hsl(208, 21%, 14%);
    border-radius: 10px;
    padding: 25px;
}
.data-flex {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
}
.icon {
    width: 50px;
    height: 50px;
    background-color: hsl(213, 19%, 18%);
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
}
h1 {
    color: hsl(0, 0%, 100%);
    font-size: 2rem;
    font-weight: 600;
    margin-bottom: 10px;
}
.card-text {
    text-align: start;
    color: hsl(217, 12%, 63%);
}
.btns {
    display: flex;
    justify-content: space-between;
    width: 100%;
}
.btns-round {
    width: 50px;
    height: 50px;
    border-radius: 50%;
    background-color: hsl(213, 19%, 18%);
    color: hsl(217, 12%, 63%);
    border: none;
    font-size: 1rem;
    font-weight: 600;
    cursor: pointer;

}

.btns-round:hover {
    background-color: hsl(25, 97%, 53%);
    color: hsl(213, 19%, 18%);
}

.btns-round:focus {
    outline: none;
    background-color: hsl(0, 0%, 100%);
    color: hsl(213, 19%, 18%);
}

.btns-round:active {
    background-color: hsl(25, 97%, 66%);
    color: hsl(213, 19%, 18%);
}

.btns-submit button{
    width: 350px;
    height: 50px;
    background-color: hsl(25, 97%, 53%);
    color: hsl(213, 19%, 18%);
    border: none;
    font-size: 1rem;
    font-weight: 800;
    cursor: pointer;
    border-radius: 40px;
}
</style>