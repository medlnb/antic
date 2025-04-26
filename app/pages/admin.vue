<script>
const UButton = resolveComponent("UButton");
import AddRoom from "../components/AddRoom.vue";

export default {
  data() {
    return {
      modalOpen: false,
      loading: true,
      data: null,
      columns: [
        {
          accessorKey: "room",
          header: "Room",
        },
        {
          accessorKey: "createdAt",
          header: "Date",
          cell: ({ row }) => {
            return new Date(row.getValue("createdAt")).toLocaleString("en-US", {
              day: "numeric",
              month: "short",
              hour: "2-digit",
              minute: "2-digit",
              hour12: false,
            });
          },
        },
        {
          accessorKey: "isNew",
          header: "New Arrival",
        },
        {
          id: "action",
        },
      ],
    };
  },
  methods: {
    async removeRoom(id) {
      this.loading = true;

      const res = await fetch(
        `https://antic-backend.vercel.app/api/room/${id}`,
        {
          method: "DELETE",
        }
      );
      this.loading = false;
      if (!res.ok)
        return this.toast.add({
          title: "Error",
          description: "Error deleting room",
          color: "error",
        });

      this.loading = false;

      this.data = this.data.filter((room) => room._id !== id);
      this.toast.add({
        title: "Room Deleted",
        description: "The room has been deleted successfully.",
        color: "success",
      });
    },
    closeModal() {
      this.modalOpen = false;
    },
  },
  async mounted() {
    this.toast = useToast();
    const response = await fetch("https://antic-backend.vercel.app/api/room");
    const json = await response.json();
    this.data = json.rooms;
    this.loading = false;
  },
  components: {
    AddRoom,
  },
};
</script>

<template>
  <UApp>
    <main class="max-w-[1140px] mx-auto px-2 py-10 pt-20">
      <div class="flex item-center justify-between pr-2 pb-2">
        <div class="flex items-center gap-2">
          <NuxtLink to="/"
            ><UButton
              icon="i-lucide-chevron-left"
              color="neutral"
              variant="ghost"
            >
            </UButton
          ></NuxtLink>
          <h1 class="lg:text-2xl">Rooms manager</h1>
        </div>
        <AddRoom
          @handleAdd="
            (room) => {
              data.unshift(room);
            }
          "
        />
      </div>

      <UTable
        :loading="loading"
        :data="data"
        :columns="columns"
        class="border border-gray-700 rounded-xl"
      >
        <template #room-cell="{ row }">
          <div class="flex items-center gap-4">
            <NuxtImg
              class="rounded-md sm:block hidden"
              :src="row.original.imageUrl"
              width="40"
              height="40"
              alt="User Avatar"
            />
            <p>{{ row.original.title }}</p>
          </div>
        </template>
        <template #isNew-cell="{ row }">
          <UIcon
            v-if="row.original.isNew"
            name="i-lucide-check"
            color="success"
          />
        </template>
        <template #action-cell="{ row }">
          <UButton
            icon="i-lucide-trash"
            color="error"
            variant="ghost"
            aria-label="Delete"
            @click="removeRoom(row.original._id)"
          />
        </template>
      </UTable>
    </main>
  </UApp>
</template>
