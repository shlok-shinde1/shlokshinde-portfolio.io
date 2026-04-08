<script setup>
const spotifyProfile = "https://open.spotify.com/user/wepbbx2slbrz4yh5iwx4oip2n"
</script>

<template>
<div class="spotify-card">
    <h3 class="title">shlk. on Spotify</h3>
    <p class="desc">
        Check out my Spotify profile and playlists.
    </p>
    <div class="actions">
        <a class="btn" :href="spotifyProfile" target="_blank" rel="noopener noreferrer">
            Open Profile
        </a>
        <a class="link" href="https://open.spotify.com/" target="_blank" rel="noopener noreferrer">
            Open Spotify Web
        </a>
    </div>
</div>
</template>

<style scoped>
.spotify-card {
    display: flex;
    flex-direction: column;
    gap: 8px;
}

.title {
    font-size: 20px;
    margin: 0;
}

.desc {
    font-size: 13px;
    margin: 0;
}

.actions {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-top: 8px;
}

.btn {
    text-decoration: none;
    color: black;
    box-shadow: 1.5px 1.5px black;
    border-top: solid rgb(250, 250, 250) 1.5px;
    border-left: solid rgb(250, 250, 250) 1.5px;
    border-bottom: solid rgb(90, 90, 90) 1.5px;
    border-right: solid rgb(90, 90, 90) 1.5px;
    background: rgb(192, 192, 192);
    padding: 4px 8px;
}

.link {
    color: #0057c2;
}
</style>
