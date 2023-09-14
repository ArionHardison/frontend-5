<template>
    <nav class="menu-secondary">
        <ul class="nav">
          <template v-if="facebook">
            <li class="nav-item">
              <a :href="facebook"><i class="fab fa-facebook-f"></i></a>
            </li>
          </template>
          <template v-if="linked">
            <li  class="nav-item">
              <a :href="linked"><i class="fab fa-linkedin-in"></i></a>
            </li>
          </template>
        </ul>
    </nav>
</template>

<script>

    export default {
        name: 'FooterMenuSecondary',
        props: {
          facebook: {
            type: [String],
          },
          linked: {
            type: [String],
          },
        }
    }
</script>
