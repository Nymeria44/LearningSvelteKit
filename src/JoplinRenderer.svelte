<!-- src/JoplinRenderer.svelte -->
<script>
  import { onMount } from "svelte";
  import { MarkupToHtml } from "joplin-renderer";

  let html = "";

  onMount(async () => {
    const options = {};
    const theme = {};
    const markdown = "Testing `MarkupToHtml` renderer";

    const markupToHtml = new MarkupToHtml(options);
    const result = await markupToHtml.render(
      MarkupToHtml.MARKUP_LANGUAGE_MARKDOWN,
      markdown,
      theme,
      options
    );

    html = result.html;

    loadPluginAssets(result.pluginAssets);
  });

  function loadPluginAssets(assets) {
    for (let i = 0; i < assets.length; i++) {
      const asset = assets[i];

      if (asset.mime === "text/css") {
        const link = document.createElement("link");
        link.rel = "stylesheet";
        link.href = "pluginAssets/" + asset.name;
        document.head.appendChild(link);
      }
    }
  }
</script>

<style>
  /* Add your component styles here */
</style>

<div bind:innerHTML={html}></div>
