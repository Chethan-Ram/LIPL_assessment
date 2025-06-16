# LIPL_assessment_1:
Explanation and Considerations:
 * Task Handles: TaskHandle_1 and TaskHandle_2 are used to reference the created tasks, essential for operations like vTaskDelete and vTaskPrioritySet.
 * Queue Handle: QueueHandle_1 is for inter-task communication. Although not explicitly used for sending/receiving in the given problem statement's conditions, it's defined as part of the setup.
 * Data_t Structure: This structure defines the format of data that would be exchanged via QueueHandle_1.
 * Global Variables: G, DataID, and DataValue are declared globally as per the problem description, implying they are shared resources accessed and modified by different parts of the system. Care must be taken in a real RTOS environment to protect access to these global variables using mutexes or semaphores to prevent race conditions. For this problem, we are just illustrating the logic based on their values.
 * vTaskDelete: When ExampleTask2 is deleted, its handle (TaskHandle_2) should be set to NULL to prevent dangling pointers and indicate that the task no longer exists. If ExampleTask2 needs to be recreated, xTaskCreate would be called again.
 * Priority Changes: vTaskPrioritySet is used to dynamically change task priorities. The priority values (3, 2, tskIDLE_PRIORITY) are examples; actual values depend on the FreeRTOS configuration (configMAX_PRIORITIES).
 * DataValue == -1 for uint8_t: As uint8_t is unsigned, it cannot represent -1 directly. If -1 is intended as a special flag, it would typically be represented by a specific uint8_t value (e.g., 255). This ambiguity highlights a common embedded system design consideration regarding data types and their interpretations.
 * Print Statements: Including print statements (printf) is crucial for debugging and observing the system's behavior. In a real embedded system, these would typically be directed to a UART or a debugger console.
 * vTaskDelay: Used to introduce delays in the tasks, allowing other tasks to run and simulating periodic behavior.
This solution provides a framework for Problem Statement 1, focusing on task and queue creation, global variable handling, and implementing the conditional logic for task deletion and priority changes as described.
