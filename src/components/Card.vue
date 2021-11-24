<template>
    <div class="card mb-4">
        <img :src="'https://source.unsplash.com/600x600/?pets,' + user.id" class="card-img-top" alt="...">
        <div class="card-body">
                <strong class="d-inline-block">{{ user.first_name }} {{ user.last_name }}</strong>
                <div class="mb-3 text-muted">{{ user.location }}</div>
                <span class="">Favourite emoji: {{ user.favourite_emoji }}</span>
                <!-- <p class="card-text mb-auto">This is a wider card with supporting text below as a natural lead-in to additional content.</p> -->
                <!-- <a href="#" class="stretched-link">Continue reading</a> -->
        </div>
    </div>
</template>

<script>
export default {
    props: {
        user: {
            type: Object,
            default: () => {},
        }
    }
}
</script>