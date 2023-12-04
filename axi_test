`include "axi_environment.sv"

class axi_test extends uvm_test;
axi_sequence (its handle);
axi_environment (its handle);
`uvm_component_utils(axi_test)

function new(string name = "name",uvm_component parent);
super.new(name,parent);
endfunction

  virtual function void build_phase(uvm_phase phase);
  super.build_phase(phase);
  axi_seq_handle = axi_sequence::type_id::create("axi_seq_handle", this);
  axi_env_handle = axi_environment::type_id::create("axi_env_handle", this);
  endfunction

virtual task run_phase(uvm_phase phase);
phase.raise_objection(this);
axi_seq_handle.start(axi_env_handle.axi_agent_handle.axi_sequencer_handle);
phase.drop_objection(this);
phase.phase_done.set_drain_time(this, 1000);
endtask  

endclass
