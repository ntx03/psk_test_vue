<script >
import Gp from './components/Gp.vue';
import data from '@/utils/data.json';
import PopupVue from './components/Popup.vue';

// сортируем дома от по порядку от 1 до 5
const gp = data.houses.sort();

export default {

  render() {
    return (
      <div class="app">
        {gp.map((i, index) => {
          return <Gp id={i} index={index} />
        })}

      </div>
    )
  }
}
</script>
<style >
.app {
  max-width: 1440px;
  display: flex;
  flex-direction: column;
  gap: 30px;
  margin: 0px auto 0px auto;

  font-family: 'Courier New', Courier, monospace;
}

.wrapper {
  display: flex;
  flex-direction: column;

}
</style>
