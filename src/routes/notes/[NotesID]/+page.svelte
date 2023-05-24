<!-- fetching information about the page from $app/stores -->
<script>
	import { page } from '$app/stores';
	const notesID = $page.params.NotesID;
</script>

<h1>You are viewing Note {notesID}</h1>
