<script setup>

import { format } from 'date-fns'

const today = format(new Date(), 'LLL. do, yyyy')

</script>

<template>
  <span>
    {{today}}
  </span>
</template>
