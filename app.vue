<template>
  <div id="app">
    <!-- Header component -->
    <header>
      <h1>Crypto Hackathon</h1>
      <p>Welcome to the Crypto Hackathon app!</p>
    </header>

    <!-- Main content section -->
    <main>
      <!-- Display list of hackathon challenges -->
      <section class="challenges">
        <h2>Challenges</h2>
        <ul>
          <li v-for="(challenge, index) in challenges" :key="index">
            <h3>{{ challenge.title }}</h3>
            <p>{{ challenge.description }}</p>
            <button @click="showChallengeDetails(index)">View Details</button>
          </li>
        </ul>
      </section>

      <!-- Display selected challenge details -->
      <section v-if="selectedChallenge" class="challenge-details">
        <h2>{{ selectedChallenge.title }}</h2>
        <p>{{ selectedChallenge.description }}</p>
        <p>Prize: {{ selectedChallenge.prize }}</p>
        <p>Deadline: {{ selectedChallenge.deadline }}</p>
        <button @click="joinChallenge(selectedChallenge)">Join Challenge</button>
      </section>

      <!-- Display list of participants and their progress -->
      <section v-if="participants.length" class="participants">
        <h2>Participants</h2>
        <ul>
          <li v-for="(participant, index) in participants" :key="index">
            <strong>{{ participant.name }}</strong> - {{ participant.progress }}
          </li>
        </ul>
      </section>
    </main>

    <!-- Footer component -->
    <footer>
      <p>&copy; {{ currentYear }} Crypto Hackathon</p>
    </footer>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      currentYear: new Date().getFullYear(),
      challenges: [
        {
          title: "Crypto Challenge 1",
          description: "Solve the cryptographic puzzle using blockchain technology.",
          prize: "500 USD in Crypto",
          deadline: "2023-08-15",
        },
        {
          title: "Crypto Challenge 2",
          description: "Create a secure decentralized application (dApp) for financial transactions.",
          prize: "1000 USD in Crypto",
          deadline: "2023-08-30",
        },
        // Add more challenges as needed
      ],
      selectedChallenge: null,
      participants: [
        {
          name: "John Doe",
          progress: "Working on Challenge 1",
        },
        {
          name: "Jane Smith",
          progress: "Completed Challenge 2",
        },
        // Add more participants as they join
      ],
    };
  },
  methods: {
    showChallengeDetails(index) {
      this.selectedChallenge = this.challenges[index];
    },
    joinChallenge(challenge) {
      // Implement logic to handle participant joining the challenge
      // For example, you can add the participant to the participants array
      // and update the progress accordingly.
    },
  },
};
</script>

<style>
/* Add your CSS styles here to customize the app's appearance */
header {
  text-align: center;
  margin-bottom: 20px;
}
main {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.challenges {
  text-align: left;
  margin-bottom: 20px;
}
.challenge-details {
  text-align: left;
  margin-bottom: 20px;
}
.participants {
  text-align: left;
}
footer {
  text-align: center;
  margin-top: 20px;
}
</style>
