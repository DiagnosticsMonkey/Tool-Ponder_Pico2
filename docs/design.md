# Design

Design files are all available in `/hardware` of the Ponder_Pico2 repository.

## Appearance

The board is _reasonably_ self-explanatory for most _intended_ users and is presented as follows:

<!-- tabs:start -->

#### **Render**

![Front of board](./assets/v1.0/Ponder-front.png ':size=300') ![Back of board](./assets/v1.0/Ponder-back.png ':size=310')

#### **Photo**

![Front of board](./assets/v1.0/frontph.jpg ':size=300') ![Back of board](./assets/v1.0/backph.jpg ':size=310')

<!-- tabs:end -->

See [here for more detail of features and usage](/features)

---

## Bill of Materials

The below is an embedded copy of the interactive bill-of-materials, available in `/hardware/outputs/bom`.

[ibom](./assets/v1.0/ibom.html ':include :type=iframe width=100% height=800px')

---

## Schematic

Whilst the majority of the expanded headers are self explanatory, the following is embedded to provide a fuller picture of the board.

Available in `/hardware/outputs`.

```pdf
./assets/v1.0/Ponder-Pico2.pdf
```

---

## Miscellaneous

The following lists any miscellany.

### Board Revision

The board includes a version and revision marker which traces back to the applicable Git commit from which the bareboard was generated.

![Revision](assets/v1.0/revision.png)

### Mod Strikes

On the rear of the board, there is a 'MODIFICATIONS' box for tracking board modifications via modification sheets, each assigned a number.
When a board is updated to a particular modification level, mark the corresponding box.

![Mod strikes](assets/v1.0/modstrike.png)

Alternatively, if a board is used in a bespoke way, check the '/CTRLD' box to indicate it is not at a known, or controlled, build level.

>[!TIP]
>The `/CTRLD` box can be useful if you have multiple boards which you're tracking the status of, but you're experimenting heavily with one and are never intending on returning it to a defined build standard.


### Serialisation

Serialisation is provided next to the Mod Strike box in the form `ZZZZ`.
