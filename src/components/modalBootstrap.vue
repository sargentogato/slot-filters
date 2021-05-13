<template>
  <div>
    <!-- Button trigger modal -->
    <button
      type="button"
      class="btn btn-primary"
      data-toggle="modal"
      data-target="#exampleModal"
    >
      Abrir Modal
    </button>

    <!-- Modal -->
    <div
      class="modal fade"
      id="exampleModal"
      tabindex="-1"
      aria-labelledby="exampleModalLabel"
      aria-hidden="true"
    >
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <slot name="headerSlot" />
          </div>
          <div class="modal-body d-flex flex-column align-items-center">
            <slot name="bodySlot" />
          </div>
          <div class="modal-footer">
            <slot name="footerSlot" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "bootstrapModal",
};
</script>

<style scoped></style>
