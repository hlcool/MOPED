LIBNAME     := liblevmar

# Sources
SOURCES.hpp := $(shell find -name "*.h")
SOURCES.o   := $(shell find -name "*.c" | grep -v core)
SOURCES.o   := $(SOURCES.o:%.c=%.o)

# Compiler flags 
CXX = g++
CXXFLAGS += -w -O3 -march=native -mfpmath=sse -fopenmp -funroll-loops
CXXFLAGS += -ffast-math -fno-trapping-math -fsingle-precision-constant

# Targets 
.PHONY: clean realclean all $(LIBNAME)
all : $(LIBNAME)

$(LIBNAME) : $(LIBNAME).a

$(LIBNAME).a : $(SOURCES.o)
	@echo [ Creating $(@F) ]
	@ar rcs $@ $(SOURCES.o)

%.o : %.c $(SOURCES.hpp)
	-@mkdir -p $(@D)
	@echo [ Compiling $(@F) ]
	@$(CXX) -fPIC $(CXXFLAGS) $(INCLUDES) -c $< -o $@

clean:
	@$(RM) -f $(SOURCES.o)

realclean:
	@$(RM) -f $(SOURCES.o) $(LIBNAME).a


	
