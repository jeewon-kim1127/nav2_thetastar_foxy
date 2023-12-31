# NOTE: The ASTAR=True does not work currently due to remapping not functioning
# All set to false, A* testing of ThetaStarPlanner happens in the planning test portion

ament_add_test(test_bt_navigator
  GENERATE_RESULT_FOR_RETURN_CODE_ZERO
  COMMAND "${CMAKE_CURRENT_SOURCE_DIR}/test_system_launch.py"
  WORKING_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}"
  TIMEOUT 180
  ENV
    TEST_DIR=${CMAKE_CURRENT_SOURCE_DIR}
    TEST_MAP=${PROJECT_SOURCE_DIR}/maps/map_circular.yaml
    TEST_WORLD=${PROJECT_SOURCE_DIR}/worlds/turtlebot3_ros2_demo.world
    GAZEBO_MODEL_PATH=${PROJECT_SOURCE_DIR}/models
    BT_NAVIGATOR_XML=navigate_w_replanning_and_recovery.xml
    ASTAR=True
    CONTROLLER=nav2_regulated_pure_pursuit_controller::RegulatedPurePursuitController
    PLANNER=nav2_theta_star_planner/ThetaStarPlanner
)

ament_add_test(test_bt_navigator_with_dijkstra
  GENERATE_RESULT_FOR_RETURN_CODE_ZERO
  COMMAND "${CMAKE_CURRENT_SOURCE_DIR}/test_system_launch.py"
  WORKING_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}"
  TIMEOUT 180
  ENV
    TEST_DIR=${CMAKE_CURRENT_SOURCE_DIR}
    TEST_MAP=${PROJECT_SOURCE_DIR}/maps/map_circular.yaml
    TEST_WORLD=${PROJECT_SOURCE_DIR}/worlds/turtlebot3_ros2_demo.world
    GAZEBO_MODEL_PATH=${PROJECT_SOURCE_DIR}/models
    BT_NAVIGATOR_XML=navigate_w_replanning_and_recovery.xml
    ASTAR=False
    CONTROLLER=dwb_core::DWBLocalPlanner
    PLANNER=nav2_theta_star_planner/ThetaStarPlanner
)

ament_add_test(test_bt_navigator_with_groot_monitoring
  GENERATE_RESULT_FOR_RETURN_CODE_ZERO
  COMMAND "${CMAKE_CURRENT_SOURCE_DIR}/test_system_launch.py"
  WORKING_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}"
  TIMEOUT 180
  ENV
    TEST_DIR=${CMAKE_CURRENT_SOURCE_DIR}
    TEST_MAP=${PROJECT_SOURCE_DIR}/maps/map_circular.yaml
    TEST_WORLD=${PROJECT_SOURCE_DIR}/worlds/turtlebot3_ros2_demo.world
    GAZEBO_MODEL_PATH=${PROJECT_SOURCE_DIR}/models
    BT_NAVIGATOR_XML=navigate_w_replanning_and_recovery.xml
    ASTAR=False
    GROOT_MONITORING=True
    CONTROLLER=dwb_core::DWBLocalPlanner
    PLANNER=nav2_theta_star_planner/ThetaStarPlanner
)

ament_add_test(test_dynamic_obstacle
  GENERATE_RESULT_FOR_RETURN_CODE_ZERO
  COMMAND "${CMAKE_CURRENT_SOURCE_DIR}/test_system_launch.py"
  WORKING_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}"
  TIMEOUT 180
  ENV
    TEST_DIR=${CMAKE_CURRENT_SOURCE_DIR}
    TEST_MAP=${PROJECT_SOURCE_DIR}/maps/map_circular.yaml
    TEST_WORLD=${PROJECT_SOURCE_DIR}/worlds/turtlebot3_ros2_demo_obstacle.world
    GAZEBO_MODEL_PATH=${PROJECT_SOURCE_DIR}/models
    BT_NAVIGATOR_XML=navigate_w_replanning_and_recovery.xml
    ASTAR=False
    CONTROLLER=dwb_core::DWBLocalPlanner
    PLANNER=nav2_theta_star_planner/ThetaStarPlanner
)

# ament_add_test(test_multi_robot
#   GENERATE_RESULT_FOR_RETURN_CODE_ZERO
#   COMMAND "${CMAKE_CURRENT_SOURCE_DIR}/test_multi_robot_launch.py"
#   WORKING_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}"
#   TIMEOUT 180
#   ENV
#     TEST_DIR=${CMAKE_CURRENT_SOURCE_DIR}
#     TEST_MAP=${PROJECT_SOURCE_DIR}/maps/map_circular.yaml
#     TEST_WORLD=${PROJECT_SOURCE_DIR}/worlds/world_only.model
#     TEST_URDF=${PROJECT_SOURCE_DIR}/urdf/turtlebot3_waffle.urdf
#     TEST_SDF=${PROJECT_SOURCE_DIR}/models/turtlebot3_waffle/model.sdf
#     BT_NAVIGATOR_XML=navigate_w_replanning_and_recovery.xml
#     CONTROLLER=dwb_core::DWBLocalPlanner
#     PLANNER=nav2_theta_star_planner/ThetaStarPlanner
# )
