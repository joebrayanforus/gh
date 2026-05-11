`timescale 1ns / 1ps

module majority_of_five_tb;

    // Inputs
    reg  [4:0] sw;

    // Outputs (must match your module!)
    wire [0:0] led;

    // Instantiate the Circuit Under Test (CUT)
    majority_of_five cut (
        .sw(sw),
        .led(led)
    );

    integer k;

    initial begin
        sw = 0;

        // Apply all 32 input combinations
        for (k = 0; k < 32; k = k + 1) begin
            #20 sw = k;
        end

        #20 $finish;
    end

endmodule


