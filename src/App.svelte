<script>
  import FeedbackList from "./components/FeedbackList.svelte";
  import Stats from "./components/Stats.svelte";
  import Form from "./components/Form.svelte";
  let feedback = [
    {
      id: 1,
      rating: 10,
      text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Quaerat praesentium ex molestiae, sunt explicabo voluptates voluptatibus consequatur eius delectus voluptatum et repellendus debitis. Nihil ex dolorum magni voluptatum eum. Cupiditate?",
    },
    {
      id: 2,
      rating: 9,
      text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Harum id odio consequuntur enim, dolorem laboriosam tempora dignissimos, quidem voluptatem pariatur delectus temporibus recusandae ipsa odit repudiandae quisquam officiis autem tenetur!",
    },
    {
      id: 3,
      rating: 6,
      text: "Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quidem iusto pariatur minima cum laudantium delectus ex ipsa accusantium dolores blanditiis voluptates nisi alias laborum molestiae molestias, dicta perferendis illum eos.",
    },
  ];

  $: count = feedback.length;

  // const rating =
  $: average =
    feedback.reduce((a, { rating }) => a + rating, 0) / feedback.length;

  const addFeedback = (e) => {
    const newFeedback = e.detail;
    feedback = [newFeedback, ...feedback];
  };

  const deleteFeedback = (e) => {
    const itemId = e.detail;
    feedback = feedback.filter((item) => item.id != itemId);
  };
</script>

<main class="container">
  <Form on:add-feedback={addFeedback} />
  <Stats {count} {average} />
  <FeedbackList {feedback} on:delete-feedback={deleteFeedback} />
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
      Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
    line-height: 1.6;
    background: #f3e8ff;
  }
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  .container {
    max-width: 768px;
    margin: 100px auto;
    padding: 0 20px;
  }
</style>
