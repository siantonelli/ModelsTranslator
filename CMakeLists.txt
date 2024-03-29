cmake_minimum_required(VERSION 3.14)
project(src)

set(CMAKE_CXX_STANDARD 17)

find_package(PkgConfig REQUIRED)
PKG_CHECK_MODULES(GLIB REQUIRED glib-2.0)
include_directories(${GLIB_INCLUDE_DIRS})
link_directories(${GLIB_LIBRARY_DIRS})

PKG_CHECK_MODULES(GLIBMM REQUIRED glibmm-2.4)
include_directories(${GLIBMM_INCLUDE_DIRS})
link_directories(${GLIBMM_LIBRARY_DIRS})

PKG_CHECK_MODULES(LIBXML++ REQUIRED libxml++-3.0)
include_directories(${LIBXML++_INCLUDE_DIRS})
link_directories(${LIBXML++_LIBRARY_DIRS})

PKG_CHECK_MODULES(LIBSBML REQUIRED libsbml)
include_directories(${LIBSBML_INCLUDE_DIRS})
link_directories(${LIBSBML_LIBRARY_DIRS})

PKG_CHECK_MODULES(SIGC++ REQUIRED sigc++-2.0)
include_directories(${SIGC++_INCLUDE_DIRS})
link_directories(${SIGC++_LIBRARY_DIRS})

include_directories(cpp)
include_directories(headers)
include_directories(parser)
include_directories(include)
include_directories(utils/exceptions)

set(SOURCE_FILES cpp/Model/Arg.cpp cpp/Model/BaseType.cpp cpp/Statements/Block.cpp cpp/Statements/Break.cpp cpp/Model/BuiltInOp.cpp cpp/Model/ConditionalExpression.cpp cpp/Model/Connection.cpp cpp/Model/Constant.cpp cpp/Model/DirConnection.cpp cpp/Statements/ElseStatem.cpp cpp/Model/Event.cpp cpp/Model/ExprVar.cpp cpp/Model/Expression.cpp cpp/Statements/ExpressionStatement.cpp cpp/Statements/ForStatem.cpp cpp/Statements/ForStatement.cpp cpp/Statements/IfStatement.cpp cpp/Model/InitAss.cpp cpp/Model/Literal.cpp cpp/Model/Module.cpp cpp/Statements/NestedStatement.cpp cpp/Model/Operation.cpp cpp/Model/OperationArg.cpp cpp/Model/OperationCall.cpp cpp/Model/Parameter.cpp cpp/Statements/Return.cpp cpp/Model/Species.cpp cpp/Statements/StNest.cpp cpp/Statements/Statement.cpp cpp/Statements/StatementOwner.cpp cpp/Statements/ThenStatem.cpp cpp/Model/Type.cpp cpp/Model/Unit.cpp cpp/Model/UserDefOp.cpp cpp/Model/Variable.cpp cpp/Statements/WhenStatem.cpp cpp/Statements/WhenStatement.cpp cpp/Statements/WhileStatem.cpp cpp/Statements/WhileStatement.cpp)

set(SOURCE_FILES ${SOURCE_FILES} headers/Model/Arg.h headers/Model/BaseType.h headers/Statements/Block.h headers/Statements/Break.h headers/Model/BuiltInOp.h headers/Model/ConditionalExpression.h headers/Model/Connection.h headers/Model/Constant.h headers/Model/DirConnection.h headers/Statements/ElseStatem.h headers/Model/Event.h headers/Model/ExprVar.h headers/Model/Expression.h headers/Statements/ExpressionStatement.h headers/Statements/ForStatem.h headers/Statements/ForStatement.h headers/Statements/IfStatement.h headers/Model/InitAss.h headers/Model/Literal.h headers/Model/Module.h headers/Statements/NestedStatement.h headers/Model/Operation.h headers/Model/OperationArg.h headers/Model/OperationCall.h headers/Model/Parameter.h headers/Statements/Return.h headers/Model/Species.h headers/Statements/StNest.h headers/Statements/Statement.h headers/Statements/StatementOwner.h headers/Statements/ThenStatem.h headers/Model/Type.h headers/Model/Unit.h headers/Model/UserDefOp.h headers/Model/Variable.h headers/Statements/WhenStatem.h headers/Statements/WhenStatement.h headers/Statements/WhileStatem.h headers/Statements/WhileStatement.h)

set(SOURCE_FILES ${SOURCE_FILES} include/AbstractAssociationLink.h include/AbstractAssociationRole.h include/ArrayIndexOutOfBoundsException.h include/DoubleOwnerAssociationLink.h include/MultiplicityConstraintException.h include/OrderedAssociationRole.h include/OrderedSet.h include/SingleOwnerAssociationLink.h include/StrongAssociationRole.h include/WeakAssociationRole.h)

set(SOURCE_FILES ${SOURCE_FILES} parser/Parser.cpp parser/Parser.h)

set(SOURCE_FILES ${SOURCE_FILES} utils/exceptions/AlgSectionException.cpp utils/exceptions/AlgorithmStatException.cpp utils/exceptions/AlreadyInModException.cpp utils/exceptions/ArrayIndexOutOfBoundsException.cpp utils/exceptions/AssInEventException.cpp utils/exceptions/BaseTypeException.cpp utils/exceptions/CondExpressionException.cpp utils/exceptions/ConditionTypeException.cpp utils/exceptions/DefInOperationException.cpp utils/exceptions/DelayTypeException.cpp utils/exceptions/ElseAlreadyInException.cpp utils/exceptions/ElseOnlyWithThenException.cpp utils/exceptions/ElseStatException.cpp utils/exceptions/EqualsVarInConnException.cpp utils/exceptions/ForIndexException.cpp utils/exceptions/InitAssException.cpp utils/exceptions/InitAssTypeException.cpp utils/exceptions/InitAssVarException.cpp utils/exceptions/IterationStatException.cpp utils/exceptions/LiteralException.cpp utils/exceptions/MultiplicityConstraintException.cpp utils/exceptions/NotInvolvedInLinkException.cpp utils/exceptions/NullPointerException.cpp utils/exceptions/OpNotInModException.cpp utils/exceptions/OperationTypeException.cpp utils/exceptions/ParameterException.cpp utils/exceptions/PriorityTypeException.cpp utils/exceptions/RemoveStatException.cpp utils/exceptions/StatInBlockException.cpp utils/exceptions/StatNotInWhenException.cpp utils/exceptions/StatemInWhenException.cpp utils/exceptions/StatementOwnerException.cpp utils/exceptions/TriggerTypeException.cpp utils/exceptions/TypeVarInConnException.cpp utils/exceptions/VarNotInModuleException.cpp utils/exceptions/WhenStatOwnerException.cpp utils/exceptions/WhileCondTypeException.cpp utils/exceptions/ArgumentInOtherFunctionException.cpp utils/exceptions/VarInAnotherModuleException.cpp utils/exceptions/StatementWithOwnerException.cpp utils/exceptions/NoStatementException.cpp utils/exceptions/NoPHMLInputException.cpp utils/exceptions/NoTypeFoundException.cpp utils/exceptions/NoUnitFoundException.cpp utils/exceptions/NoIDException.cpp utils/exceptions/NoModuleFoundException.cpp utils/exceptions/NoVariableFoundException.cpp utils/exceptions/NoModuleConnectionException.cpp utils/exceptions/NotSupportedException.cpp)

set(SOURCE_FILES ${SOURCE_FILES} main.cpp)

set(SOURCE_FILES ${SOURCE_FILES} toModelica/model2Modelica.cpp toModelica/model2Modelica.h)

add_executable(src ${SOURCE_FILES})

target_link_libraries(src ${GLIB_LIBRARIES})
target_link_libraries(src ${GLIBMM_LIBRARIES})
target_link_libraries(src ${LIBXML++_LIBRARIES})
target_link_libraries(src ${LIBSBML_LIBRARIES})
target_link_libraries(src ${SIGC++_LIBRARIES})