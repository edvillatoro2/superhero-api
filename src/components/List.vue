<template>
    <div v-for="list in lists" :key="list.id" class="heroes-list">
        <div class="card">
            <div class="card-image">
                <img :src="list.images.md" alt="superheros" class="card__image">
            </div>

            <div class="card__overlay">
                <div class="card__header">
                    <div class="card__header-text">
                        <h3>{{list.name}}</h3>
                        <h4><span>Full Name:</span> {{list.biography['fullName']}}</h4>
                        <h4><span>Alter Egos:</span> {{list.biography['alterEgos']}}</h4>
                    </div>
                </div>
                <div class="card__description">
                    <ul>
                        <li><strong>Strength:</strong> {{list.powerstats['strength']}}</li>
                        <li><strong>Power:</strong> {{list.powerstats['power']}}</li>
                        <li><strong>Intelligence:</strong> {{list.powerstats['intelligence']}}</li>
                        <li><strong>Combat:</strong> {{list.powerstats['combat']}}</li>
                        <li><strong>Speed:</strong> {{list.powerstats['speed']}}</li>
                        <li><strong>Durability:</strong> {{list.powerstats['durability']}}</li>
                    </ul>
                    <p><strong>Gender:</strong> {{list.appearance['gender']}}</p>
                    <p><strong>Weight:</strong> {{list.appearance['weight']}}</p>
                    <p><strong>Place of Birth:</strong> {{list.biography['placeOfBirth']}}</p>
                    <p><strong>First Appearance:</strong> {{list.biography['firstAppearance']}}</p>
                    <p><strong>Publisher:</strong> {{list.biography['publisher']}}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
name: 'List',
data() {
    return {
        lists: [],
        }
    },
    mounted() {
        axios.get('https://akabab.github.io/superhero-api/api/all.json')
        .then((response) => {
                this.lists = response.data
            })
            .catch((error) => {
                console.log(error)
            })
    }
}
</script>

<style scoped>
* {
    margin: 0;
    padding: 0;
    letter-spacing: 2px;
    line-height: 1.2;
}

h3 {
    color: rgba(16, 106, 134, 0.9);
    font-size: 1.4rem;
}

span {
    color: rgb(161, 62, 62);
}

.card {
    position: relative;
    display: block;
    height: 100%;  
    border-radius: 10px;
    overflow: hidden;
    text-decoration: none;
    box-shadow: 5px 5px 30px 7px rgba(0,0,0,0.25), -5px -5px 30px 7px rgba(0,0,0,0.22);
    transition: 0.4s;
    border-radius: 5px;
}

.card:hover {
    transform: scale(0.9, 0.9);
    box-shadow: 5px 5px 30px 15px rgba(0,0,0,0.25), 
    -5px -5px 30px 15px rgba(0,0,0,0.22);
    }

.card__image {
  width: 100%;
  height: auto;
}

img {
    object-fit: cover;
}

.card__overlay {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 1;      
  border-radius: 5px;   
  background-color: white;      
  transform: translateY(100%);
  transition: .4s ease-in-out;
}

.card:hover .card__overlay {
  transform: translateY(0);
}

.card__header {
    position: relative;
    display: flex;
    align-items: center;
    gap: 2em;
    padding: 2em;
    background-color: white;
    transform: translateY(-100%);
    transition: .2s ease-in-out;
}

.card:hover .card__header {
  transform: translateY(0);
}

.card__description {
  padding: 0 2rem 1rem;
  margin: 0;
  color: rgba(161, 62, 62, 0.5);
  overflow: hidden;
  list-style-type: none;
}

@media only screen and (max-width: 900px) {
  .card__description {
    font-size: 18px;
    padding: 0 1rem 1rem;
    font-size: 0.9rem;
    line-height: 0;
    letter-spacing: 0;
  }
}

li {
    list-style-type: none;
}

</style>