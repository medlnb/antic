<template>
  <UModal v-model:open="DialogToggle" title="Add new Room">
    <UButton
      icon="i-lucide-plus"
      color="neutral"
      variant="outline"
      label="Add Room"
    />
    <template #body>
      <label for="file" class="mx-auto block">
        <div
          class="mx-auto w-44 h-66 border border-white border-dotted text-xs rounded-xl flex items-center justify-center hover:opacity-40 duration-300 cursor-pointer overflow-hidden"
        >
          <p v-if="imageStatus === 'loading'">loading</p>
          <p v-if="!imageUrl && imageStatus !== 'loading'" class="text-center">
            Click to add your room image
          </p>
          <NuxtImg
            v-if="imageUrl && imageStatus === 'success'"
            :src="imageUrl"
            class="w-full h-full object-cover"
            alt="Uploaded Image"
          ></NuxtImg></div
      ></label>
      <input
        id="file"
        type="file"
        @change="handleUpload"
        :multiple="false"
        class="hidden"
      />
      <br />
      <UInput v-model="title" class="w-full" placeholder="Title..." color="" />
    </template>
    <template #footer>
      <div class="flex justify-end w-full">
        <UButton
          label="Submit"
          color="neutral"
          :loading="loading"
          :disabled="loading"
          @click="handleSubmit"
        />
      </div>
    </template>
  </UModal>
</template>

<script>
export default {
  data() {
    return {
      DialogToggle: false,
      imageUrl: "",
      title: "",
      imageStatus: null,
      loading: false,
    };
  },
  mounted() {
    this.toast = useToast();
  },
  methods: {
    async handleUpload(e) {
      try {
        const file = e.target.files[0];
        if (!file) return alert("Please select a file");

        this.imageStatus = "loading";

        const data = new FormData();
        data.append("my_file", file);
        const res = await fetch("http://localhost:4000/api/image", {
          method: "POST",
          body: data,
        });

        if (!res.ok) {
          this.imageStatus = "error";
          this.toast.add({
            title: "Error",
            description: "Failed to upload image.",
            color: "error",
          });
          return;
        }
        this.imageStatus = "success";
        const json = await res.json();
        this.imageUrl = json.url;
        this.toast.add({
          title: "Success",
          description: "Image Added successfully.",
          color: "success",
        });
      } catch (error) {
        this.imageStatus = "error";
        alert(error.message);
      }
    },
    async handleSubmit() {
      if (!this.title || !this.imageUrl) return alert("Please fill all fields");
      this.loading = true;
      const res = await fetch("http://localhost:4000/api/room", {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          title: this.title,
          imageUrl: this.imageUrl,
        }),
      });
      this.loading = false;
      if (!res.ok)
        return this.toast.add({
          title: "Error",
          description: "Failed to create room.",
          color: "error",
        });

      const json = await res.json();
      this.DialogToggle = false;
      this.$emit("handleAdd", { ...json, isNew: true });
      this.toast.add({
        title: "Success",
        description: "Room Created successfully.",
        color: "success",
      });
      this.title = "";
      this.imageUrl = "";
    },
  },
};
</script>
