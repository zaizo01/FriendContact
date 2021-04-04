<template>
    <li>
        <h2>{{ name }} {{ isFavorite ? '(Favorite)' : ''}}</h2>
        <button @click="toggleFavorite">Toggle Favorite</button>
        <button @click="toggleDetails">{{ detailsAreVisable ? 'Hide' : 'Show' }} Details</button>
        <button @click="$emit('delete-contact', id)">Delete</button>
        <ul v-if="detailsAreVisable">
            <li>
                <strong>Phone:</strong>
                {{ phoneNumber }}
            </li>
            <li>
                <strong>Email:</strong>
                {{ email}}
            </li>
        </ul>
    </li>
</template>

<script>
export default {
    // props: ['name', 'phoneNumber', 'email', 'isFavorite'],
    props: {
        id: {
            type: String,
            required: true
        },
        name: {
            type: String,
            required: true
        },
        phoneNumber: {
            type: String,
            required: true
        },
        email: {
            type: String,
            required: true
        },
        isFavorite: {
            type: Boolean,
            required: false,
            default: false,
            // validator:  function(value) {
            //     return value === '1' || value === '0';
            // }
        }
    },
    emits: ['toggle-favorite', 'delete-contact'],
    // emits: {
    //     'toggle-favorite': function (id) {
    //         if (id) {
    //             return true;
    //         } else {
    //             console.log('id is missing!!');
    //             return false;
    //         }
    //     }
    // },
    data() {
        return {
            detailsAreVisable: false,
        }
    },
    methods: {
        toggleDetails(){
            this.detailsAreVisable = !this.detailsAreVisable;
        },
        toggleFavorite(){
            this.$emit('toggle-favorite', this.id);
        },
        // deleteContact(){
        //     this.$emit('delete-contact', this.id)
        // }
    },
}
</script>

