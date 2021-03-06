#Makefile for the Bose-Hubbard Case Study Wrapper
#----------------------------------------------
OFLAGS = -O3 -ffree-line-length-none #Set the optimization flags
LIBFLAGS = -llapack -lblas #Link the LAPACK and BLAS libraries
MC=gfortran

#-----------------------------------
#List objects
#-----------------------------------
OBJS = system_parameters.o TEBDtools_module.o io_module.o Hamiltonian_tools_module.o bose_hubbard_module.o fermi_hubbard_module.o heisenberg_module.o spinS_module.o rotation_module.o local_operations_module.o observables_module.o  propagation_module.o  

#-----------------------------------
#Object compilation rules
#-----------------------------------


#Modules	
system_parameters.o : system_parameters.f90
		$(MC) $(OFLAGS) -c system_parameters.f90

TEBDtools_module.o : ../../VidalCore_v_2.0/TEBDtools_module.f90
		$(MC) $(OFLAGS) -c ../../VidalCore_v_2.0/TEBDtools_module.f90

io_module.o : ../../ToolsCore_v_2.0/io_module.f90
		$(MC) $(OFLAGS) -c ../../ToolsCore_v_2.0/io_module.f90
		
Hamiltonian_tools_module.o : ../../HamiltonianCore_v_2.0/Hamiltonian_tools_module.f90
		$(MC) $(OFLAGS) -c ../../HamiltonianCore_v_2.0/Hamiltonian_tools_module.f90

bose_hubbard_module.o : ../../HamiltonianCore_v_2.0/bose_hubbard_module.f90
		$(MC) $(OFLAGS) -c ../../HamiltonianCore_v_2.0/bose_hubbard_module.f90

fermi_hubbard_module.o : ../../HamiltonianCore_v_2.0/fermi_hubbard_module.f90
		$(MC) $(OFLAGS) -c ../../HamiltonianCore_v_2.0/fermi_hubbard_module.f90

heisenberg_module.o : ../../HamiltonianCore_v_2.0/heisenberg_module.f90
		$(MC) $(OFLAGS) -c ../../HamiltonianCore_v_2.0/heisenberg_module.f90

spinS_module.o : ../../HamiltonianCore_v_2.0/spinS_module.f90
		$(MC) $(OFLAGS) -c ../../HamiltonianCore_v_2.0/spinS_module.f90

rotation_module.o : ../../HamiltonianCore_v_2.0/rotation_module.f90
		$(MC) $(OFLAGS) -c ../../HamiltonianCore_v_2.0/rotation_module.f90

local_operations_module.o : ../../VidalCore_v_2.0/local_operations_module.f90
		$(MC) $(OFLAGS) -c ../../VidalCore_v_2.0/local_operations_module.f90

observables_module.o : ../../VidalCore_v_2.0/observables_module.f90
		$(MC) $(OFLAGS) -c ../../VidalCore_v_2.0/observables_module.f90

propagation_module.o : ../../VidalCore_v_2.0/propagation_module.f90
		$(MC) $(OFLAGS) -c ../../VidalCore_v_2.0/propagation_module.f90


#Main Programs	
BoseHubbard_ITP.o : BoseHubbard_ITP.f90
		$(MC) $(OFLAGS) -c BoseHubbard_ITP.f90

BoseHubbard_Quench.o : BoseHubbard_Quench.f90
		$(MC) $(OFLAGS) -c BoseHubbard_Quench.f90



#-----------------------------------
#Primary rules
#-----------------------------------

ITP :  $(OBJS) BoseHubbard_ITP.o
	$(MC) $(OFLAGS)  -o Execute_ITP BoseHubbard_ITP.o $(OBJS) $(LIBFLAGS)

Quench :  $(OBJS) BoseHubbard_Quench.o
	$(MC) $(OFLAGS)  -o Execute_Quench BoseHubbard_Quench.o $(OBJS) $(LIBFLAGS)

clean: #removes all old *.o and *.mod files
	rm *.o
	rm *.mod
	rm Execute*

touch : #go through all of the *.f90 source files in the Core folders, touching them (updating the timestamp, forcing 'make' to recompile them)
	touch *.f90
	cd ../../VidalCore_v_2.0/
	touch *.f90
	cd ../../ToolsCore_v_2.0/
	touch *.f90
	cd ../../HamiltonianCore_v_2.0/
	touch *.f90


	
