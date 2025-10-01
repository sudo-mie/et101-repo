# et101-repo


Actually for parentQty, instead of hardcode as a constant, you can direct extract from the parentOrder.

E.g. final int parentQty = AreAlgoVerifierTableJoiner.getParentOrderInputTable(context).get(0).getValue(SIZE);

You can continue use constant for the max rate constrained qty, e.g. final long maxParticipationRateConstrainedQty = 500L;

