<template>
    <div class="Specimen">
        <div class="col l3 m6">
            <div v-if="specimen != null" class="card card-small" @click="goToDetails()">
                <div class="card-title">
                    <h4>{{ specimen.Title }}</h4>
                </div>
                <div class="card-image">
                    <img
                        :src="
                            'http://site.local:8081/api/assets/crystal-catalog/' +
                            specimen.Thumbnail[0]
                        "
                        class="responsive"
                    />
                </div>
                <div class="card-content">
                    <dl class="dl-inline">
                        <dt>Type</dt>
                        <dd>{{ specimen.Identification }}</dd>
                        <dt>Color</dt>
                        <dd>{{ specimen.Color }}</dd>
                        <dt>Shape</dt>
                        <dd>{{ specimen.Shape }}</dd>
                        <dt>Size</dt>
                        <dd>{{ specimen.Size }}</dd>
                    </dl>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Specimen",
    props: {
        id: String,
        specimen: Object,
    },
    methods: {
        goToDetails () {
            this.$router.push('/details/' + this.id);
        }
    }
};
</script>