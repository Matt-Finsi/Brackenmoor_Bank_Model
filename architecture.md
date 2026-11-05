# arch notes (not official)

this is my read of the model from poking at the inference box and the files.
nobody on the team wrote this down, so some of it is guesses.

- byte-level. the input is just bytes, no tokenizer merges as far as i can tell.
- looks like a small decoder-only transformer: embedding, 2 blocks, final norm, linear head.
- hidden size 96, 4 heads, context 96. i read this off config.json and the tensor shapes.
- the mlp in each block expands to 384 and back down.
- output is 256 logits, one per byte value. no bias on the head.
- served with greedy decoding, from what i saw in generation_config.json.

if the numbers are wrong, the config is the source of truth, not me.
