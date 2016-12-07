static int
foo_stub_unwind_sniffer (const struct frame_unwind *self,
                           struct frame_info *this_frame,
                           void **this_prologue_cache)
{
  CORE_ADDR addr_in_block;

  addr_in_block = get_frame_address_in_block (this_frame);
  if (in_plt_section (addr_in_block, NULL))
    return 1;

  return 0;
}

struct frame_unwind foo_stub_unwind = {
  NORMAL_FRAME,
  foo_stub_this_id,
  foo_frame_prev_register,
  NULL,
  foo_stub_unwind_sniffer
};
