# Calculated meter User Manual


## Key rules

- Calculated meters ONLY handles events after lock date on the calculated meter. All events before lock date are omitted. 
- To be able to run the formula and store a meter value for the calculated meter, **ALL** inputs for the given timestamp and resolution **MUST** have a value. The function **MUST** return a scalar value. If these conditions are true, the calculated value is stored.
- All calculations overwrites current calculated value.
- Deletion of an inputs value causes the calculated value to be deleted as well. This is recursive.
- On calculated meter delete, no further calculations will be done for it.
- On formula change, the formula updates. All meter values from the calculated meter lock date are recalculated using the new formula.
- On formula error, all calculated values for that meter will be set 0,

### Recalculation of meter values for calculated meters occurs when:

- Any input changes
- Input sort order changes
- Any input value changes
- Formula changes
- Lock date for the calculated meter changes
- Factor of the meter changes
- Factor of an input changes