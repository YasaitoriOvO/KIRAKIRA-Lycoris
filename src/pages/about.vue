<script setup lang="ts">
const branch = computed(() => {
  const items: string[] = [];
  if (import.meta.env.VITE_BACKEND_URI.includes("localhost")) items.push("Local Backend");
  else if (import.meta.env.VITE_BACKEND_URI.includes("kirakira")) items.push("Live");
  else if (import.meta.env.VITE_BACKEND_URI === "none") items.push("No Backend");
  if (import.meta.env.DEV) items.push("Dev");
  if (typeof BRANCH !== "undefined") items.push(BRANCH);
  if (typeof COMMIT_REF !== "undefined") items.push(COMMIT_REF);
  return items.join(" ");
});
</script>

<template>
	<div class="container">
		<Logo :width="400" />
		<div class="mlb-4">
			<NTag type="info">
				<template #icon>
					<Icon name="forkRight" />
				</template>
				{{ branch }}
			</NTag>
		</div>

		<NH4>GitHub</NH4>
		<NFlex>
			<NButton dashed color="#00dc82" tag="a" target="_blank" href="https://github.com/KIRAKIRA-DOUGA/KIRAKIRA-Cerasus">Cerasus</NButton><!-- Color of Nuxt -->
			<NButton dashed color="#3178c6" tag="a" target="_blank" href="https://github.com/KIRAKIRA-DOUGA/KIRAKIRA-Rosales">Rosales</NButton><!-- Color of TypeScript -->
			<NButton dashed color="#63e2b7" tag="a" target="_blank" href="https://github.com/KIRAKIRA-DOUGA/KIRAKIRA-Lycoris">Lycoris</NButton><!-- Color of Naive UI -->
		</NFlex>

		<NH4>Powered by</NH4>
		<NFlex>
			<NButton dashed color="#63e2b7" tag="a" target="_blank" href="https://www.naiveui.com/">Naive UI</NButton>
		</NFlex>
	</div>
</template>
