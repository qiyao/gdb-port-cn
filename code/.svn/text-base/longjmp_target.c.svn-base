static int
foo_get_longjmp_target (struct frame_info *frame, CORE_ADDR *pc)
{
  struct gdbarch *gdbarch = get_frame_arch (frame);
  enum bfd_endian byte_order = gdbarch_byte_order (gdbarch);
  CORE_ADDR jb_addr;
  char buf[4];

  /* JMP_BUF is passed by reference in R4.  */
  jb_addr = get_frame_register_unsigned (frame, 4);

  /* JMP_BUF contains 13 elements of type int, and return address is stored
     in the last one.  */
  if (target_read_memory (jb_addr + 12 * 4, buf, 4))
    return 0;

  *pc = extract_unsigned_integer (buf, 4, byte_order);

  return 1;
}
