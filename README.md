import java.io.BufferedReader
import java.io.InputStreamReader

fun runCommand(command: String): String {
    val process = Runtime.getRuntime().exec(command)
    val reader = BufferedReader(InputStreamReader(process.inputStream))
    val output = StringBuilder()
    var line: String? = reader.readLine()
    while (line != null) {
        output.append(line).append("\n")
        line = reader.readLine()
    }
    process.waitFor()
    return output.toString()
}

fun main() {
    println(runCommand("git add ."))
    println(runCommand("""git commit -m "توضیح تغییرات""""))
    println(runCommand("git push origin main"))
}
