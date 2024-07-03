<template>
    <div class="container">
        <div class="row gap-2 justify-content-center ">
            <Card v-for="emp in employees" :key="emp.id">
                <h4 class="display-4">{{ emp.firstName }} {{ emp.lastName }}</h4>
                <button class="btn btn-primary" :id="`employee${emp.id}`"
                    @click.prevent="showDetails($event, JSON.stringify(emp))">Show</button>
            </Card>
        </div>
    </div>
</template>

<script>
import Card from './Card.vue'
export default {
    name: "EmployeeComp",
    components: {
        Card
    },
    data() {
        return {
            count: 0,
            employees: [
                {
                    id: 1,
                    firstName: 'Peter',
                    lastName: 'John',
                    profile: 'https://codjoelmayer.github.io/projectImages/images/profile-Image.png'
                },
                {
                    id: 2,
                    firstName: 'Joel',
                    lastName: 'Mukanya',
                    profile: 'https://codjoelmayer.github.io/projectImages/images/joel1.jpg'
                },
                {
                    id: 3,
                    firstName: 'Matthew',
                    lastName: 'Brown',
                    profile: 'https://codjoelmayer.github.io/projectImages/images/profile-Image.png'
                }
            ]
        }
    },
    methods: {
        showDetails(event, employee) {
            let cButton = event.target
            let data = JSON.parse(employee)
            if ((+cButton.id.at(-1) == data.id) && (this.count == 0)) {
                cButton.insertAdjacentHTML('afterend', `
                    <div>
                        <img src="${data.profile}" alt="${data.firstName}" loading="lazy" class="img-fluid"/>
                    </div>
                `)
                cButton.innerText = "Hide"
                this.count++
            } else {
                location.reload()
                cButton.innerText = "Show"
                this.count = 0
            }
        }
    }
}
</script>

<style scoped></style>