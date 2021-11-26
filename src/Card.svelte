<script>
  export let suit;
  export let num;

  let asciiCards = [
    "🃑 🃒 🃓 🃔 🃕 🃖 🃗 🃘 🃙 🃚 🃛 🃝 🃞",
    "🂱 🂲 🂳 🂴 🂵 🂶 🂷 🂸 🂹 🂺 🂻 🂽 🂾",
    "🂡 🂢 🂣 🂤 🂥 🂦 🂧 🂨 🂩 🂪 🂫 🂭 🂮",
    "🃁 🃂 🃃 🃄 🃅 🃆 🃇 🃈 🃉 🃊 🃋 🃍 🃎",
  ];
  function getAsciiCard(suit, num) {
    return asciiCards[suit].split(" ")[num];
  }
</script>

<p class="bigCard" class:red={"24".includes(suit)}>
  {getAsciiCard(parseInt(suit) - 1, parseInt(num) - 1)}
</p>

<style>
  .bigCard {
    font-size: 10rem;
    margin: 0;
    padding: 0;
  }
  .red {
    color: red;
  }
</style>
