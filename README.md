# Blobify

A lightweight, robust, and secure dynamic memory management library written in C. It provides an abstraction layer over raw memory blocks (`blb_block_t`), allowing users to define safe boundaries (`blb_range_t`) and navigate through them using a flexible pointer tracker (`blb_cursor_t`).

Combined together, these structures form a **Blob**—a powerful composite object designed for safe byte-level memory reading, writing, and navigation without risking buffer overflows or memory leaks.

---

## Features

- **Safe Memory Blocks**: Automatic initialization (`memset` to `0`) and bounds-checked operations.
- **Dynamic Range Slicing**: Define precise start points and sizes within memory, with support for resizing and sliding.
- **Protected Cursor Tracking**: Jump or step through your memory layout without ever going out of bounds.
- **Memory Leak Protection**: Built-in cascade memory cleanup patterns for all inner components.
- **Visual Debugger**: Built-in printer that shows exactly where your cursor is currently pointing in the data pipeline.

---

## Project Structure

```text
├── blobify.c    # Implementation of blocks, ranges, cursors, and blobs
├── blobify.h    # Structures definitions, constants, and function prototypes
└── main.c       # Quick start/testing environment

API Reference
1. Blob Architecture

    blb_blob_create(uint32_t size, uint8_t step): Allocates and initializes a new compound blob container.

    blb_blob_delete(blb_blob_t *blob): Safely deallocates the container and all its internal sub-components.

    blb_blob_jump(blb_blob_t *blob, uint32_t value): Moves the cursor directly to a specific offset if within range limits.

    blb_blob_step(blb_blob_t *blob, int32_t step): Moves the cursor forward or backward by a delta step.

    blb_blob_put(blb_blob_t *blob, uint8_t value): Writes a byte at the current cursor position.

    blb_blob_get(blb_blob_t *blob, uint8_t *value): Reads a byte from the current cursor position.

    blb_blob_print(blb_blob_t *blob, FILE *output): Outlines the active buffer stream with a localized <- Cursor tracker pointer
