In the evaluation, you show that SGD has a more stable validation loss curve compared to adam, however that same stability is not evident in the model loss graphs shown, why is this?

This is because this test was done during the early stages using more epochs, however when it came to the later stages, i notice my models were doing better with less training, so less epochs, thus it is more difficult to visualise .. soethinglie this