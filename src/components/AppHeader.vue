<script>
export default {
    name: 'AppHeader',
    data() {
        return {
            menuLinks: [
                {
                    text: 'Home',
                    rootName: 'home'
                },
                {
                    text: 'About',
                    rootName: 'about'
                },
                {
                    text: 'Projects',
                    rootName: 'projects'
                },
            ]
        };
    }
}
</script>

<template>
    <header>
        <nav class="navbar navbar-expand-lg bg-light">
            <div class="container-fluid">
                <a class="navbar-brand" href="#">Navbar</a>
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarNav">
                    <ul class="navbar-nav">
                        <li v-for="link in menuLinks" class="nav-item">
                            <router-link class="nav-link" aria-current="page" :to="{name: link.rootName}">{{ link.text }}</router-link>
                        </li>
                    </ul>
                </div>
            </div>
        </nav>
    </header>
</template>