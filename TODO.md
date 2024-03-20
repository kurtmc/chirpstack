# TODO

- Add migration, actually I don't think this is needed, instead just use the emit_xxx column to store the emit time and just add the absolute_time field to the protobuf interface:
    - ALTER TABLE public.multicast_group_queue_item ADD absolute_time int8 NULL;

