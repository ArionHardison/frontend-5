<template>
    <div class="meta">
        <p>
            <span class="date">{{ fromIso(program.created_at).day }}</span> {{ fromIso(program.created_at).monthShort}}</span>
        </p>
    </div>
</template>

<script>
    import time from "../../../mixins/time";
    export default {
        name: 'Meta',
        mixins: [time],
        props: {
          program: {
            type: Object,
            default: {}
          }
        }
    }
</script>
