<template>
    <div class="details" v-if="specimen != null">
        <br /><br />
        <div class="row">
            <div class="col l5 offset-l1">
                <div v-if="specimen.Images.length > 0">
                    <Slider :imageIds="specimen.Images[0].Image" />
                </div>
                <div v-else>
                    <img
                        :src="
                            'http://site.local:8081/api/assets/crystal-catalog/' +
                            specimen.Thumbnail[0]
                        "
                        class="responsive"
                    />
                </div>
            </div>
            <div class="col l3 offset-l1">
                <h1>{{ specimen.Title }}</h1>
                <div>
                    <ul class="list-group striped">
                        <li>
                            <strong>Type:</strong> {{ specimen.Identification }}
                        </li>
                        <li><strong>Color:</strong> {{ specimen.Color }}</li>
                        <li><strong>Shape:</strong> {{ specimen.Shape }}</li>
                        <li><strong>Size:</strong> {{ specimen.Size }}</li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Slider from "@/components/Slider.vue";

export default {
    name: "Details",
    data() {
        return {
            id: this.$route.params.id,
            info: null,
            specimen: null,
        };
    },
    components: {
        Slider,
    },
    methods: {
        fetchItems() {
            fetch(process.env.VUE_APP_API_ROOT + "specimen/" + this.id, {
                headers: {
                    Authorization: process.env.VUE_APP_API_KEY,
                    "X-Flatten": "true",
                },
            })
                .then((response) => response.json())
                .then((data) => (this.info = data))
                .then((data) => (this.specimen = data.data));
        },
    },
    mounted() {
        this.fetchItems();
    },
};
</script>

