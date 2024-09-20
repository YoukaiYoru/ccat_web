<template>
    <v-card
    class="searching-bar"
    >
        <v-card-text>
            <v-text-field
            v-model="searchingBar"
            :loading="loading"
            density="compact"
            variant="solo"
            label="Buscar"
            append-inner-icon="mdi-magnify"
            single-line
            hide-details
            clearable
            @click:append-inner="onClick"
            ></v-text-field>
            <v-spacer></v-spacer>
            <v-card-action class="d-flex flex-row-reverse">
                <v-btn class="mt-4">Pasados</v-btn>
                <v-btn class="mt-4 mr-4">Activos</v-btn>
            </v-card-action>
        </v-card-text>

    </v-card>
        
    <v-sheet>
        <v-slide-group v-model="slide" show-arrows="hover"
        >
            <v-slide-group-item v-for="event in events" :key="event.id">
                <v-card
                color="grey-lighten-1"
                class="ma-4"
                height="200"
                width="200">
                    <v-img
                    :src="event.image"
                    height="100%"
                    cover></v-img>
                </v-card>
            </v-slide-group-item>
        </v-slide-group>
    </v-sheet>
    <v-sheet>
        <v-row>
            <v-col>
                <v-chip-group class="justify-center">
                    <v-chip 
                    v-for="area in areasfilter"
                    :key="area.id"
                    label
                    size="x-large"
                    class="chip-areas">
                        {{ area.title }}
                    </v-chip>
                </v-chip-group>
            </v-col>
        </v-row>
    </v-sheet>
    <v-container class="align-center">
            <v-row class="justify-center">
                <v-col
                cols="10"
                class="justify-center">
                <eventComp 
                v-for="event in events"
                :key="event.id"
                :title="event.title"
                :hour="event.time"
                :date="event.date"
                :eventImage="event.image"
                :tag="event.tag"
                />
                </v-col>
            </v-row>    


    </v-container>

</template>

<script setup>
    import { ref } from 'vue';
    import eventComp from '@/components/Events/EventComp.vue'


    const slide =ref(null)
    const searchingBar = ref('');

    const loaded =ref(false);
    const loading = ref(false);

    const onClick = () => {
        loading.value = true;
        
        setTimeout(() => {
            loading.value = false;
            loaded.value = true;
        }, 2000)
    };


    //Events 
	const events = ref(

	[
		{id:1, title:'título 1', time:'hhmmss', date:'dd/mm/yyyy' , image:'./src/assets/patata.jpg', tag:'área1' },
		{id:2, title:'título 2', time:'hhmmss', date:'dd/mm/yyyy' , image:'./src/assets/patata.jpg', tag:'área2'  },
		{id:3, title:'título 3', time:'hhmmss', date:'dd/mm/yyyy' , image:'./src/assets/patata.jpg', tag:'área3'  },
		{id:4, title:'título 4', time:'hhmmss', date:'dd/mm/yyyy' , image:'./src/assets/patata.jpg', tag:'área4'  },
		{id:5, title:'título 5', time:'hhmmss', date:'dd/mm/yyyy' , image:'./src/assets/patata.jpg', tag:'área5'  },
		{id:6, title:'título 6', time:'hhmmss', date:'dd/mm/yyyy' , image:'./src/assets/patata.jpg', tag:'área6'  },
        {id:7, title:'título 7', time:'hhmmss', date:'dd/mm/yyyy' , image:'./src/assets/patata.jpg', tag:'área6'  },
        {id:7, title:'título 8', time:'hhmmss', date:'dd/mm/yyyy' , image:'./src/assets/patata.jpg', tag:'área6'  },
        {id:7, title:'título 9', time:'hhmmss', date:'dd/mm/yyyy' , image:'./src/assets/patata.jpg', tag:'área6'  },
        {id:7, title:'título 10', time:'hhmmss', date:'dd/mm/yyyy' , image:'./src/assets/patata.jpg', tag:'área6'  },
        {id:7, title:'título 11', time:'hhmmss', date:'dd/mm/yyyy' , image:'./src/assets/patata.jpg', tag:'área6'  },

	]
	)

    //Areas filter

    const areasfilter=ref(
        [
            {id:1, title:'Academia'},
            {id:2, title:'Investigación'},
            {id:3, title:'Tec. de información'},
            {id:4, title:'Gest. del Talento Humano'},
            {id:5, title:'Logística'},
            {id:6, title:'CODE'}
        ]
    )



</script>

<style scoped>

.searching-bar{
    background-color:#D9E8F6;
    border-radius: 0px;
}
.chip-areas{
    background-color: #1B263B;
	color: white;
    
}

</style>
