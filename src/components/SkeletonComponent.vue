<template>
  <div class="container">
    <div class="img-section"></div>
    <div class="content-section">
      <div>
        <h1
          style="
            background-color: var(--light-gray-color);
            width: 500px;
            height: 40px;
          "
        ></h1>
        <div
          class="flex justify-between item-center"
          style="
            padding: 14px 0;
            border-bottom: 2px solid var(--light-gray-color);
            margin-top: 10px;
          "
        >
          <p
            style="
              background-color: var(--light-gray-color);
              width: 100px;
              height: 20px;
            "
          ></p>
          <div class="flex item-center" style="gap: 2px">
            <p
              style="
                margin-right: 2px;
                background-color: var(--light-gray-color);
                width: 50px;
                height: 20px;
              "
            ></p>
            <div
              style="
                background-color: var(--light-gray-color);
                width: 100px;
                height: 20px;
              "
            ></div>
          </div>
        </div>
        <div style="padding: 20px 0">
          <div
            style="
              background-color: var(--light-gray-color);
              width: 100%;
              height: 20px;
            "
          ></div>
          <div
            style="
              background-color: var(--light-gray-color);
              width: 100%;
              height: 20px;
              margin-top: 8px;
            "
          ></div>
          <div
            style="
              background-color: var(--light-gray-color);
              width: 50%;
              height: 20px;
              margin-top: 8px;
            "
          ></div>
        </div>
        <div
          style="
            font-size: 28px;
            font-weight: bold;
            color: var(--light-gray-color);
            padding: 14px 0;
            margin-top: 20px;
            border-top: 2px solid var(--light-gray-color);
            width: 100px;
            height: 70px;
          "
        >
          <div
            style="
              background-color: var(--light-gray-color);
              width: 100px;
              height: 100%;
            "
          ></div>
        </div>
        <div class="flex" style="gap: 12px">
          <div
            style="
              width: 100%;
              padding: 12px 0;
              border: none;
              background-color: var(--light-gray-color);
              color: white;
              font-size: larger;
              height: 50px;
            "
          ></div>
          <div
            style="
              width: 100%;
              padding: 12px 0;
              border: 4px solid var(--light-gray-color);
              background-color: transparent;
              color: var(--light-gray-color);
              font-size: larger;
              font-weight: bold;
              height: 50px;
            "
          ></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SkeletonComponent",
};
</script>

<style scoped>
img {
  width: 100%;
  height: 100%;
  aspect-ratio: initial;
}
h1 {
  font-size: 30px;
}
.container {
  display: flex;
  justify-content: space-between;
  width: 900px;
  min-height: 70vh;
  gap: 32px;
  background-color: white;
  padding: 40px;
  box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.4);
}

.img-section {
  width: 250px;
  height: 300px;
  background-color: var(--light-gray-color);
}

.flex {
  display: flex;
}

.justify-between {
  justify-content: space-between;
}

.item-center {
  align-items: center;
}
</style>
