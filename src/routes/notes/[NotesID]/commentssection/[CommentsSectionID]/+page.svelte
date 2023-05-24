<!-- fetching information about the page from $app/stores -->
<script>
	import { page } from '$app/stores';
	const { NotesID, CommentsSectionID } = $page.params;
</script>

<h1>This is the comment Section {CommentsSectionID} for note {NotesID}</h1>
