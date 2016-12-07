static int
thumb_in_function_epilogue_p (struct gdbarch *gdbarch, CORE_ADDR pc)
{
  /* inst1 is read from PC.  */
  if ((inst1 & 0xff80) == 0x4700)
    /* BX lr is typically used for returns.  */
    found_return = 1;

  if (!found_return)
    return 0;

  /* inst2 is read from PC - 2.  */
  if ((inst2 & 0xff00) == 0xbc00)
    /* POP (without PC).  */
    found_stack_adjust = 1;

  if (found_stack_adjust)
    return 1;

  return 0;
}
